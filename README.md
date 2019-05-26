# Faulty records search

## How to run it
------

1. Download this repository
```bash
git clone https://github.com/evemorgen/amidp-project.git
cd amidp-project
```
2. Prepare virtualenv
```bash
python3 -m venv ENV
```

3. Install dependecies
```bash
python -m pip install -r requirements.txt
```

4. Run it
```bash
python faulty_records_search.py --help
usage: faulty_records_search.py [-h] [-d DIRECTORY] [-o OUTPUT]

Script for filtering faulty records in provided dataset

optional arguments:
  -h, --help            show this help message and exit
  -d DIRECTORY, --directory DIRECTORY
                        Directory containing csv files. Script searches for
                        csv's recursively
  -o OUTPUT, --output OUTPUT
                        Output file where report will be saved
```

5. Example run:
```bash
python faulty_records_search.py --directory '**/BITalino/*.csv'
2019-05-25 15:40:41 pc67.home root[43033] INFO [2/104] processing data/2018-afcai-spring/B303/BITalino/GSR_p.csv
2019-05-25 15:40:41 pc67.home root[43032] INFO [1/104] processing data/2018-afcai-spring/B303/BITalino/BPM_p.csv
2019-05-25 15:40:41 pc67.home root[43034] INFO [3/104] processing data/2018-afcai-spring/B305/BITalino/BPM.csv
2019-05-25 15:40:41 pc67.home root[43035] INFO [4/104] processing data/2018-afcai-spring/B305/BITalino/GSR.csv
2019-05-25 15:40:42 pc67.home root[43032] WARNING [over irq threshold] data/2018-afcai-spring/B303/BITalino/BPM_p.csv contained 66194 values outside IRQ, which is 10% of values
```

## Obtained results

Desired report file will be written to location specified by `--output` flag (defaults to `report.txt`)

Report file has the following structure:
  - it contains `INFO` entry about files it performed checks on
  - it contains `WARNING` entries regarding check failing on specific file

That structure makes it easy enough to use standard `grep` filters, for example
```bash
cat report.txt | grep 'over 50'
WARNING:root:[over 50% same values] /Volumes/SD/AfCAI 2018 wyniki eksperymentu/2018-afcai-spring/B325/BITalino/GSR.csv contained 681 different values, 99.68% of them was 1020.0
WARNING:root:[over 50% same values] /Volumes/SD/AfCAI 2018 wyniki eksperymentu/2018-afcai-spring/B362/BITalino/GSR.csv contained 454 different values, 52.94% of them was 1020.0
WARNING:root:[over 50% same values] /Volumes/SD/AfCAI 2018 wyniki eksperymentu/2018-afcai-spring/B372/BITalino/GSR.csv contained 1 different values, 100.0% of them was 1020.0
WARNING:root:[over 50% same values] /Volumes/SD/AfCAI 2018 wyniki eksperymentu/2018-afcai-spring/B388/BITalino/GSR.csv contained 295 different values, 51.29% of them was 1020.0
WARNING:root:[over 50% same values] /Volumes/SD/AfCAI 2018 wyniki eksperymentu/2018-afcai-spring/D313/BITalino/GSR.csv contained 258 different values, 81.97% of them was 1020.0
```
