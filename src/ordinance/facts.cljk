(ns ordinance.facts
  "Municipal-ordinance compliance catalog for Tokyo (東京都) -- the
  municipality-level counterpart to cloud-itonami-iso3166-jpn's
  `statute.facts` (national law). Per ADR-2607141700
  (cloud-itonami-compliance-fact-federation): each entry cites an
  OFFICIAL Tokyo Metropolitan Government ordinance-database URL
  (https://www.reiki.metro.tokyo.lg.jp/) -- never fabricated. An
  ordinance not in this table has NO spec-basis, full stop; extend
  `catalog`, do not invent an id/url/number.

  Every URL below was independently WebFetch-verified against the live
  reiki.metro.tokyo.lg.jp page on 2026-07-14 (title + ordinance number +
  enactment date read back from the actual document, not guessed).")

(def catalog
  "municipality-slug -> vector of ordinance entries."
  {"tokyo"
   [{:ordinance/id "tokyo.info-disclosure"
     :ordinance/title "東京都情報公開条例 (Tokyo Metropolitan Information Disclosure Ordinance)"
     :ordinance/municipality "tokyo"
     :ordinance/country "JPN"
     :ordinance/kind :ordinance
     :ordinance/number "条例第五号"
     :ordinance/url "https://www.reiki.metro.tokyo.lg.jp/reiki/reiki_honbun/g101RG00000214.html"
     :ordinance/url-provenance :official-reiki-database
     :ordinance/enacted-date "1999-03-19"
     :ordinance/retrieved-at "2026-07-14"
     :ordinance/topic #{:information-disclosure :transparency}}
    {:ordinance/id "tokyo.appi-implementation"
     :ordinance/title "個人情報の保護に関する法律施行条例 (Ordinance for Implementation of the Act on Protection of Personal Information)"
     :ordinance/municipality "tokyo"
     :ordinance/country "JPN"
     :ordinance/kind :ordinance
     :ordinance/number "条例第一三〇号"
     :ordinance/url "https://www.reiki.metro.tokyo.lg.jp/reiki/reiki_honbun/g101RG00005236.html"
     :ordinance/url-provenance :official-reiki-database
     :ordinance/enacted-date "2022-12-22"
     :ordinance/retrieved-at "2026-07-14"
     :ordinance/topic #{:data-protection :privacy}}]})

(defn spec-basis [muni] (get catalog muni))

(defn coverage
  ([] (coverage (keys catalog)))
  ([munis]
   (let [have (filter catalog munis)
         missing (remove catalog munis)]
     {:requested (count munis)
      :covered (count have)
      :covered-municipalities (vec (sort have))
      :missing-municipalities (vec (sort missing))
      :note (str "cloud-itonami-municipality-jpn-tokyo Wave 0 (ADR-2607141700): "
                 (count (get catalog "tokyo")) " Tokyo ordinances seeded with an "
                 "official reiki.metro.tokyo.lg.jp citation. Extend "
                 "`ordinance.facts/catalog`, never fabricate an ordinance id/url.")})))

(defn by-topic [muni topic]
  (filterv #(contains? (:ordinance/topic %) topic) (spec-basis muni)))
