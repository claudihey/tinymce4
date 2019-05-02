# TinyMCE4-Editor für REDAXO 5

## Default-Profil

```yml
{
selector: 'textarea.tinyMCEEditor',
file_browser_callback: redaxo5FileBrowser,
plugins: 'advlist autolink lists link image charmap print preview anchor searchreplace visualblocks code fullscreen insertdatetime media table contextmenu paste code',
toolbar: 'insertfile undo redo | styleselect | bold italic | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | link image',
convert_urls: false,
content_css: '/assets/addons/tinymce4/bootstrap/css/bootstrap.min.css',
}
```

Wichtig: **redaxo5FileBrowser** ist eine Funktion. Darum werden an dieser Stelle **keine Quotes** verwendet. 

## Empfehlungen

### convert_urls: false

Wenn `convert_urls: true` ist, dann verändert Tinymce eingegebene URLs beim speichern. Zum Beispiel wird eine URL `/media/xxx` in `../media/xxx` umgewandelt. Dies ist meistens nicht gewünscht, daher sollte `convert_urls: false` im Profil enthalten sein (beim Default-Profil ist das schon drin).

Weitere Infos zum Thema: https://www.tinymce.com/docs/configure/url-handling/

### Bootstrap-Tabellenlayout im edit

Damit die Bootstrap-Tabellenklassen rsp. auch die Bootstrap-Bilder-Klassen im Editor verfügbar sind, kann das folgende Snippet dem Profil hinzu gefügt werden:

```yml
table_class_list: [
    {title: 'None', value: ''},
    {title: 'Table', value: 'table'},
    {title: 'Table striped', value: 'table-striped'}
], 
image_advtab: true,
image_class_list: [
    {title: 'None', value: ''},
    {title: 'Abgerundet', value: 'img-rounded'},
    {title: 'Kreis', value: 'img-circle'},
    {title: 'Responsive', value: 'img-responsive'}
]
```
### Ergänzung des Color-Pickers

```selector: 'textarea.tinyMCEEditor',
file_browser_callback: redaxo5FileBrowser,
plugins: 'advlist autolink lists link image charmap print preview anchor searchreplace visualblocks code fullscreen insertdatetime media table contextmenu paste code textcolor',
toolbar: 'insertfile undo redo | styleselect | bold italic | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | link image | forecolor backcolor',

textcolor_map: [
"000000", "Black",
"FF6600", "Orange",
"008000", "Green",
"0000FF", "Blue",
"808080", "Gray",
"FF0000", "Red",
"FFFFFF", "White"
],

convert_urls: false,
content_css: '../assets/addons/tinymce4/bootstrap/css/bootstrap.min.css'
}```

Mit textcolor_map kann man eigene Farben definieren, lässt man den Eintrag weg, werden Standard-Farben verwendet.
