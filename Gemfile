source "https://rubygems.org"

# Usa a mesma stack que o GitHub Pages compila no servidor.
# Para preview local: `bundle install` e depois `bundle exec jekyll serve`.
gem "github-pages", group: :jekyll_plugins
gem "jekyll-remote-theme"

# Dependências de plataforma (Windows/JRuby)
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end
gem "wdm", "~> 0.1.1", platforms: [:mingw, :x64_mingw, :mswin]
