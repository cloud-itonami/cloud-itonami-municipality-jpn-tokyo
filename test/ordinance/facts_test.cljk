(ns ordinance.facts-test
  (:require [kotoba.lang.text :as str]
            [clojure.test :refer [deftest is]]
            [ordinance.facts :as facts]))

(deftest tokyo-has-spec-basis
  (let [sb (facts/spec-basis "tokyo")]
    (is (= 2 (count sb)))
    (is (every? #(str/starts-with? (:ordinance/url %) "https://www.reiki.metro.tokyo.lg.jp/") sb))
    (is (every? :ordinance/number sb))))

(deftest unknown-municipality-has-no-spec-basis
  (is (nil? (facts/spec-basis "osaka")))
  (is (nil? (facts/spec-basis "zzz"))))

(deftest coverage-is-honest
  (let [c (facts/coverage ["tokyo" "osaka"])]
    (is (= 2 (:requested c)))
    (is (= 1 (:covered c)))
    (is (= ["osaka"] (:missing-municipalities c)))))

(deftest by-topic-filters
  (is (= ["tokyo.appi-implementation"]
         (mapv :ordinance/id (facts/by-topic "tokyo" :data-protection))))
  (is (empty? (facts/by-topic "tokyo" :labor)))
  (is (empty? (facts/by-topic "osaka" :data-protection))))
