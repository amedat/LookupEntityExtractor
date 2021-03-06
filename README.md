# Lookup Entity Extractor

Lookup Entity Extractor built for Rasa for extracting known entities from a list of examples without the need for training on every set of examples. The extractor is not machine-learned but uses text-matching logic for entity prediction. It doesn't discover any additional values other than the provided list of examples.

Lookup Entity Extractor is a good fit when you have list of exampless that are known and can be expanded as required.

The list examples required for the extractor is same as [Lookup Tables](https://rasa.com/docs/rasa/nlu/training-data-format/#lookup-tables)

### How to setup?

- **Step 1**: copy the `CustomEntityExtractor.py` in your project directory
- **Step 2**: configure the `Lookup Entity Extractor` in the `config.yml` along with the required parameters i.e `entities`(list of entity names) & `files_path`:(path for the data files)
```
  # https://rasa.com/docs/rasa/nlu/components/
  language: en
  pipeline:
    - name: WhitespaceTokenizer
    - name: RegexFeaturizer
    - name: LexicalSyntacticFeaturizer
    - name: CountVectorsFeaturizer
    - name: CountVectorsFeaturizer
      analyzer: "char_wb"
      min_ngram: 1
      max_ngram: 4
    - name: DIETClassifier
      epochs: 100
      # entity_recognition: False
    - name: EntitySynonymMapper
    - name: ResponseSelector
      epochs: 100
    - name: CustomEntityExtractor.LookupEntityExtractor
      entities: ["pokemon_name"]
      files_path: ["data/pokenames.txt"]

```

- **Step 3**: Now you can train the model and test the `Lookup Entity Extractor`

### Sample Bot

https://github.com/JiteshGaikwad/pokedex-demo

### Demo

https://youtu.be/S9_Y08DxkCo

