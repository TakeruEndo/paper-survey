## jekyll + Github Pages

```
# 2.5.0だとうまくローカルサーバーを立ち上げられなかった
$ rbenv install 2.4.0
# ver確認
$ rbenv versions
$ rvenv global 2.4.0
$ mkdir ~/.rbenv/versions/paper-survey
$ ruby-build 2.4.0 ~/.rbenv/versions/paper-survey

$ bundle install
$ gem install gekyll
$ jekyll serve

```

## pagenationの導入
http://jekyllrb-ja.github.io/docs/pagination/
`_config.yml`
```
plugins:
  - jekyll-paginate

paginate: 6
paginate_path: "page:num"
```

```
$ gem install jekyll-paginate 
# 起動
$ bundle exec jekyll serve
```

## 参考にしたjekyllテンプレート
http://jekyllthemes.org/themes/sleek/  

## categoryの取得
```
{% for category in site.categories %}
  <li class="category-head">
    <a href="">
      <span class="right">{{ category_name }}</span>
      <span class="right">[{{site.categories[category_name].size}}]</span>
    </a>
  {% capture category_name %}{{ category | first }}{% endcapture %}
{% endfor %}
```
