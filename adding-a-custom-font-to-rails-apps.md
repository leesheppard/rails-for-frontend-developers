# Adding custom fonts

**For Rails 4.1 and higher.**

Create a folder name `fonts` inside the `app/assets` directory and place custom fonts inside this new folder. The folder structure should now look like `app/assets/fonts`.

Add this line to `config/application.rb`:

```ruby
config.assets.paths << Rails.root.join("app", "assets", "fonts")
```

Rename `app/assets/stylesheets/application.css` to `app/assets/stylesheets/application.css.scss`. Place your font css code into this file. An example below shows you what the structure would look like.

You can cut and paste this example code but remember to replace `custom-font-name` with your font name. And change the font-family name to the font name of your choosing:

```css
@font-face {
    font-family: 'Custom Font Title';
    src: url(asset-path("custom-font-name.eot"));
    src: url(asset-path("custom-font-name.eot?#iefix"))  format("embedded-opentype"),
          url(asset-path("custom-font-name.woff2")) format("woff2"),
          url(asset-path("custom-font-name.woff")) format("woff"),
          url(asset-path("custom-font-name.ttf")) format("truetype"),      
          url(asset-path("custom-font-name.svg#custom-font-name")) format("svg");
    }
```

Now add fonts to `config/initializers/assets.rb` to precompile additional assets.

```ruby
Dir.glob("#{Rails.root}/app/assets/fonts/**/").each do |path|
    Rails.application.config.assets.paths << path
end
```

Then restart the web server and test.

```bash
$ bundle exec rails s
```

