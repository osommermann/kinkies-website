# Webseite für `kinkies.de`

Die Quellen der Webseite verwenden das Format
[Markdown](https://pandoc.org/MANUAL.html#pandocs-markdown)
in der erweiterten Variante von `pandoc`. Die
Website besteht aus drei verlinkten Seiten:

- `index.md`: Startseite mit Auftrag, Kontakt und Stellenangeboten
- `ueber-uns.md`: Team, Pädagogik und Aktivitäten
- `kontakt.md`: Kontakt, Vereinsregister und Zuordnung der Domain zum Verein

Alle HTML-Seiten können mit denselben Befehlen wie im GitHub-Pages-Build erzeugt werden:

```sh
mkdir -p _site
rsync -a --exclude='.git' --exclude='.github' --exclude='_site' \
      --exclude='*.md' ./ _site/
for f in *.md; do
  [ "$f" = "README.md" ] && continue
  pandoc --standalone "$f" -o "_site/${f%.md}.html"
done
```

Für eine lokale Vorschau:

```sh
python3 -m http.server 8000 --directory _site
```

Anschließend <http://localhost:8000> öffnen. Die HTML-Dateien sind Build-Artefakte;
Änderungen werden in den Markdown-Quellen vorgenommen.

Die Vereinsangaben nennen das Registergericht und die Vereinsregisternummer.
Sie enthalten bewusst keine persönlichen Daten von Vorstandsmitgliedern und
sind nicht als vollständig rechtlich geprüftes Impressum zu verstehen.
Die Vereinsregisternummer ist kein eigenständiger Nachweis der steuerlichen
Gemeinnützigkeit. Falls Google eine andere Kennung verlangt, muss diese anhand
der bereits genehmigten Registrierung geklärt werden.
