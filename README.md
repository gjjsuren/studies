# studies

ml.t3.medium","ml.m5.large","ml.m5.xlarge","ml.m5.2xlarge"
1. Maak een repo aan in Gitlab
2. Start een code editor op in AWS
3. Zorg ervoor dat AWS bij de repo kan door in .netrc het de personal access token op te slaan   nano ~/.netrc   Plak het volgende erin (cntrl-X -> Y -> Enter):     machine hollandcasino.gitlab.host     login _token_     password <your_token>
4. Clone de repo door:   
    * kopieer de https link in het code menu in Gitlab (in de relevante repo)   
    * navigeer naar juiste map   
    * git clone  <https>
    * configureer git <https link>     git config --global user.name "Gijsbert Suren"     git config --global user.email "g.suren@hollandcasino.nl"   
    * upgrade pip : pip install --upgrade pip   
    * installeer uv : pip install uv   
        * initieer uv : uv init --package   
        * Synchronize the project dependencies: uv sync   
    * Installeer pre-commit: python      
        * create the pre-commit config : pre-commit sample-config > .pre-commit-config.yaml    
          * pre-commit sample-config | out-file .pre-commit-config.yaml -encoding utf8 
        * pas deze aan door het te vervangen door:

# See https://pre-commit.com for more information
# See https://pre-commit.com/hooks.html for more hooks
repos:
- repo: https://github.com/pre-commit/pre-commit-hooks
  rev: v5.0.0
  hooks:
    - id: trailing-whitespace
    - id: end-of-file-fixer
    - id: check-yaml
    - id: check-added-large-files
- repo: https://github.com/astral-sh/uv-pre-commit
  rev: 0.6.12
  hooks:
    - id: uv-lock
- repo: https://github.com/astral-sh/ruff-pre-commit
  rev: v0.11.3
  hooks:
    - id: ruff
      args: [--fix]
    - id: ruff-format
- repo: https://github.com/pre-commit/mirrors-mypy
  rev: 'v1.15.0'
  hooks:
    - id: mypy
      args: [--strict,--ignore-missing-imports]
      additional_dependencies: [pydantic, pydantic-settings]


        * enable pre-commit : pre-commit install     
        * update hooks automatically (versies enzo): pre-commit autoupdate     
    * maak iig de volgende subdirectories : mkdir notebooks docs tests     
    * installeren packages (iig pytest) : uv add --dev pytest       uv add pandas         
    * list packages : pip list   
    * run main : uv run main.py
    * om system resources te monitoren gebruik : htop   
        * installeer door : sudo apt-get install htop Gecompliceerde queries. Moeten we dit server side doen of in een code editor machine? vroeger deed je dit soort queries server side (sql optimale manier om met data om te gaan), nu los binnen trekken? of toch lange sql queries als literals in code? .sh in standaard setup (gelijk ook navigeren juiste map?)
