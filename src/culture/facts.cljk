(ns culture.facts
  "Regional-culture catalog for Tokyo (東京都) -- local dishes,
  protected products, beverages, festivals and heritage sites, piggybacked
  onto this municipality compliance repo per ADR-2607171400
  (cloud-itonami-municipality-culture-catalog, in com-junkawasaki/root),
  sibling namespace to `ordinance.facts` (ADR-2607141700).

  Every entry cites a source URL that was actually fetched and read on
  :culture/retrieved-at -- never fabricated. Summaries state only what the
  cited source confirms. An item not in this table has NO spec-basis, full
  stop; extend `catalog`, do not invent an id/url.")

(def catalog
  "municipality-slug -> vector of culture entries."
  {"tokyo"
   [{:culture/id "tokyo.dish.monjayaki"
     :culture/name "Monjayaki"
     :culture/name-local "もんじゃ焼き"
     :culture/municipality "tokyo"
     :culture/country "JPN"
     :culture/kind :dish
     :culture/summary "Pan-fried batter dish popular in the Kanto region, said to have originated in Tokyo's Tsukishima district; runnier than the similar okonomiyaki."
     :culture/url "https://en.wikipedia.org/wiki/Monjayaki"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "tokyo.dish.chankonabe"
     :culture/name "Chankonabe"
     :culture/name-local "ちゃんこ鍋"
     :culture/municipality "tokyo"
     :culture/country "JPN"
     :culture/kind :dish
     :culture/summary "Stew commonly eaten in vast quantities by sumo wrestlers; the first chankonabe restaurant opened in 1937 in Tokyo's Ryogoku district."
     :culture/url "https://en.wikipedia.org/wiki/Chankonabe"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "tokyo.dish.fukagawa-meshi"
     :culture/name "Fukagawa-meshi"
     :culture/name-local "深川めし"
     :culture/municipality "tokyo"
     :culture/country "JPN"
     :culture/kind :dish
     :culture/summary "Clam-and-shellfish rice dish served over or mixed with rice, named after the Fukagawa district of Tokyo's Koto ward."
     :culture/url "https://ja.wikipedia.org/wiki/%E6%B7%B1%E5%B7%9D%E3%82%81%E3%81%97"
     :culture/url-provenance :wikipedia-ja
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "tokyo.product.tsukudani"
     :culture/name "Tsukudani"
     :culture/name-local "佃煮"
     :culture/municipality "tokyo"
     :culture/country "JPN"
     :culture/kind :product
     :culture/summary "Preserved food of thinly sliced seafood, meat or seaweed simmered in soy sauce and mirin, originating from Tsukudajima island in present-day Chuo, Tokyo, during the Edo period."
     :culture/url "https://en.wikipedia.org/wiki/Tsukudani"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "tokyo.beverage.hoppy"
     :culture/name "Hoppy"
     :culture/name-local "ホッピー"
     :culture/municipality "tokyo"
     :culture/country "JPN"
     :culture/kind :beverage
     :culture/summary "Beer-flavored, almost non-alcoholic drink (0.8% alcohol) produced since 1948, most popular in Tokyo where it remains a staple of izakaya pubs."
     :culture/url "https://en.wikipedia.org/wiki/Hoppy_(drink)"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "tokyo.craft.edo-kiriko"
     :culture/name "Edo kiriko"
     :culture/name-local "江戸切子"
     :culture/municipality "tokyo"
     :culture/country "JPN"
     :culture/kind :craft
     :culture/summary "Style of cut glass, now a traditional Japanese craft, that originated in Edo (modern-day Tokyo) during the 19th century, known for intricately cut bold geometric patterns."
     :culture/url "https://en.wikipedia.org/wiki/Edo_kiriko"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "tokyo.festival.sanja-matsuri"
     :culture/name "Sanja Matsuri"
     :culture/name-local "三社祭"
     :culture/municipality "tokyo"
     :culture/country "JPN"
     :culture/kind :festival
     :culture/summary "One of the three largest Shinto festivals in Tokyo, held annually on the third weekend of May at Asakusa Shrine with portable-shrine processions."
     :culture/url "https://en.wikipedia.org/wiki/Sanja_Matsuri"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "tokyo.heritage.senso-ji"
     :culture/name "Senso-ji"
     :culture/name-local "浅草寺"
     :culture/municipality "tokyo"
     :culture/country "JPN"
     :culture/kind :heritage
     :culture/summary "Ancient Buddhist temple in Asakusa and Tokyo's oldest-established temple, one of the most widely visited religious sites in the world."
     :culture/url "https://en.wikipedia.org/wiki/Sens%C5%8D-ji"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}]})

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
      :note (str "cloud-itonami-municipality-jpn-tokyo culture catalog "
                 "(ADR-2607171400): " (count (get catalog "tokyo"))
                 " Tokyo entries, each with a fetched-and-read citation. "
                 "Extend `culture.facts/catalog`, never fabricate an id/url.")})))

(defn by-kind [muni kind]
  (filterv #(= (:culture/kind %) kind) (spec-basis muni)))
