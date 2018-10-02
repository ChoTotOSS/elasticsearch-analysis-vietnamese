Vietnamese Analysis Plugin for Elasticsearch
========================================

Vietnamese Analysis plugin integrates Vietnamese language analysis into Elasticsearch.

In order to install the plugin, choose a version in [releases](https://github.com/duydo/elasticsearch-analysis-vietnamese/releases) page then run:

```sh
bin/plugin install link/to/binary/version
```

Or to build from source, you need to build it with Maven:

```bash
mvn clean package
bin/plugin install file:target/releases/elasticsearch-analysis-vietnamese-5.2.0.zip
```

*Notes*: To build the plugin you need to clone and build the [vn-nlp-libararies](https://github.com/ChoTotOSS/vn-nlp-libraries.git). The plugin uses  [Lê Hồng Phương](http://mim.hus.vnu.edu.vn/phuonglh/) vnTokenizer library. Thanks thầy Lê Hồng Phương for great contribution.


|Vietnamese Analysis Plugin|Elasticsearch|
|---|---|
| master|5.2.0|
| 2.4.1|2.4.1|
| 2.4.1|2.4.1|
| 2.4.0|2.4.0|
| 2.3.5|2.3.5|
| 2.3.4|2.3.4|
| 2.3.3|2.3.3|
| 2.3.2|2.3.2|
| 2.3.1|2.3.1|
| 2.3.0|2.3.0|
| 0.2.2|2.2.0|
| 0.2.1.1|2.1.1|
| 0.2.1|2.1.0|
| 0.2|2.0.0|
| 0.1.7|1.7+|
| 0.1.6|1.6+|
| 0.1.5|1.5+|
| 0.1.1|1.4+|
| 0.1|1.3|

## Build guide

In case you want to customize vn-nlp or this plugin (add more stopword or token)

### Presequisite:
[Maven](http://maven.apache.org/download.cgi)

### Build vn-nlp-libraries
```bash
git clone https://github.com/ChoTotOSS/vn-nlp-libraries.git
cd vn-nlp-libraries
mvn compile
mvn package
```

### Build elasticsearch-vietnamese-analysis
```bash
git clone https://github.com/ChoTotOSS/elasticsearch-analysis-vietnamese.git
cd elasticsearch-analysis-vietnamese
mvn compile
mvn package
```
There will be a file in target/releases/elasticsearch-analysis-vietnamese-5.2.0.zip
Because ES 5.x requires plugins file should be under folder name `elasticsearch`. So we need an extra step:

``` bash
mkdir elasticsearch && mv elasticsearch-analysis-vietnamese-5.2.0.zip elasticsearch
cd elasticsearch && unzip elasticsearch-analysis-vietnamese-5.2.0.zip
rm elasticsearch-analysis-vietnamese-5.2.0.zip && cd ..
zip -r elasticsearch-analysis-vietnamese-5.2.0.zip elasticsearch
```


## User guide

The plugin provides the `vi_analyzer` analyzer and `vi_tokenizer` tokenizer.

The `vi_analyzer` is built using the `vi_tokenizer` tokenizer, the `lowercase` and `stop` filter.

 The analyzer analyzes `"công nghệ thông tin Việt Nam"` into `"công nghệ thông tin"` and `"việt nam"` tokens.

## Thanks to
- [Lê Hồng Phương](http://mim.hus.vnu.edu.vn/phuonglh/) for his VnTokenizer library
- [JetBrains](https://www.jetbrains.com) has provided a free license for their great tool: [IntelliJ IDEA](https://www.jetbrains.com/idea/)

## Authors

This work is based on the original repository https://github.com/duydo/elasticsearch-analysis-vietnamese/
whose author is [Duy Do](https://github.com/duydo/).

License
-------

    This software is licensed under the Apache 2 license, quoted below.

    Licensed under the Apache License, Version 2.0 (the "License"); you may not
    use this file except in compliance with the License. You may obtain a copy of
    the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
    WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
    License for the specific language governing permissions and limitations under
    the License.
