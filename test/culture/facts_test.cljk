(ns culture.facts-test
  (:require [clojure.edn :as edn]
            [kotoba.lang.text :as str]
            [clojure.test :refer [deftest is]]
            [culture.facts :as facts]))

(deftest tokyo-has-culture-basis
  (let [sb (facts/spec-basis "tokyo")]
    (is (= 8 (count sb)))
    (is (= (count sb) (count (set (map :culture/id sb)))))
    (is (every? #(str/starts-with? (:culture/url %) "https://") sb))
    (is (every? #(= "tokyo" (:culture/municipality %)) sb))
    (is (every? #(= "JPN" (:culture/country %)) sb))
    (is (every? #(seq (:culture/summary %)) sb))
    (is (every? #(string? (:culture/retrieved-at %)) sb))))

(deftest unknown-municipality-has-no-basis
  (is (nil? (facts/spec-basis "osaka")))
  (is (nil? (facts/spec-basis "zzz"))))

(deftest coverage-is-honest
  (let [c (facts/coverage ["tokyo" "osaka"])]
    (is (= 2 (:requested c)))
    (is (= 1 (:covered c)))
    (is (= ["osaka"] (:missing-municipalities c)))))

(deftest by-kind-filters
  (is (= 3 (count (facts/by-kind "tokyo" :dish))))
  (is (= ["tokyo.beverage.hoppy"]
         (mapv :culture/id (facts/by-kind "tokyo" :beverage))))
  (is (= ["tokyo.craft.edo-kiriko"]
         (mapv :culture/id (facts/by-kind "tokyo" :craft))))
  (is (empty? (facts/by-kind "osaka" :dish))))

(deftest tx-file-matches-catalog
  (let [tx (edn/read-string (slurp "data/culture-tx.edn"))
        flat (mapcat val (sort-by key facts/catalog))]
    (is (= (vec flat) (vec tx)))))
