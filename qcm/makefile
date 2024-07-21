# Nom du dossier de sortie
OUTPUT_DIR = build

# Nom du fichier principal (à remplacer par le nom de votre fichier principal sans extension)
MAIN = main

# Crée le dossier de sortie s'il n'existe pas
$(OUTPUT_DIR):
	mkdir -p $(OUTPUT_DIR)

# Cibles par défaut
all:
	pdflatex $(OUTPUT_DIR)/filename.tex
	pdflatex $(OUTPUT_DIR)/filename.tex
	open $(OUTPUT_DIR)/filename.pdf

# Cible pour nettoyer les fichiers auxiliaires
clean:
	rm -f $(OUTPUT_DIR)/*.aux $(OUTPUT_DIR)/*.log $(OUTPUT_DIR)/*.toc $(OUTPUT_DIR)/*.blg $(OUTPUT_DIR)/*.out $(OUTPUT_DIR)/*.bbl
	rm -f $(OUTPUT_DIR)/*.synctex.gz


# Générer un PDF à partir d'un fichier .tex
%.pdf: %.tex | $(OUTPUT_DIR)
	@echo '.........: pdflatex running pass 1...'
	pdflatex -shell-escape -output-directory=$(OUTPUT_DIR) $< -o $@ 2>&1 | tee errors.err
	@echo '.........: pdflatex running pass 2...'
	pdflatex -shell-escape -output-directory=$(OUTPUT_DIR) $< -o $@ 2>&1 | tee errors.err
	@echo '.........: pdflatex run finished.'

