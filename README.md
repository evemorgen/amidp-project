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
```
python -m pip install -r requirements.txt
```

4. Run it
```
python faulty_records_search.py -h              130 ↵
usage: faulty_records_search.py [-h] [-d DIRECTORY]

Script for filtering faulty records in provided dataset

optional arguments:
  -h, --help            show this help message and exit
  -d DIRECTORY, --directory DIRECTORY
                        Directory containing csv files. Script searches for
                        csv's recursively
```

5. Example run:
```
python faulty_records_search.py --directory '**/BITalino/*.csv'
2019-05-25 15:40:41 pc67.home root[43033] INFO [2/104] processing data/2018-afcai-spring/B303/BITalino/GSR_p.csv
2019-05-25 15:40:41 pc67.home root[43032] INFO [1/104] processing data/2018-afcai-spring/B303/BITalino/BPM_p.csv
2019-05-25 15:40:41 pc67.home root[43034] INFO [3/104] processing data/2018-afcai-spring/B305/BITalino/BPM.csv
2019-05-25 15:40:41 pc67.home root[43035] INFO [4/104] processing data/2018-afcai-spring/B305/BITalino/GSR.csv
2019-05-25 15:40:42 pc67.home root[43032] WARNING [over irq threshold] data/2018-afcai-spring/B303/BITalino/BPM_p.csv contained 66194 values outside IRQ, which is 10% of values
```