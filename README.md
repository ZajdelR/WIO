function GetLatestReleaseInfo() {
  $.getJSON("https://api.github.com/repos/ShareX/ShareX/releases/latest").done(function(release) {
    var asset = release.assets[0];
    var downloadCount = 0;
    for (var i = 0; i < release.assets.length; i++) {
      downloadCount += release.assets[i].download_count;
    }
    var oneHour = 60 * 60 * 1000;
    var oneDay = 24 * oneHour;
    var dateDiff = new Date() - new Date(asset.updated_at);
    var timeAgo;
    if (dateDiff < oneDay) {
      timeAgo = (dateDiff / oneHour).toFixed(1) + " hours ago";
    } else {
      timeAgo = (dateDiff / oneDay).toFixed(1) + " days ago";
    }
    var releaseInfo = release.name + " was updated " + timeAgo + " and downloaded " + downloadCount.toLocaleString() + " times.";
    $(".download").attr("href", asset.browser_download_url);
    $(".release-info").text(releaseInfo);
    $(".release-info").fadeIn("slow");
  });
}

GetLatestReleaseInfo();

<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>

# WIO
Wprowadzenie do Inżynierii Oprogramowania | semestr 4

Folder zawiera wykłady, cwiczenia oraz liste zadan do sprawozdan

Aby otowrzyć wyklad w formacie HTML bezpośrednio w przeglądarce, otwieramy go w formacie raw i dodajemy:

http://htmlpreview.github.io/?

jako prefix otwartego adresu url


http://htmlpreview.github.io/?raw.githubusercontent.com/ZajdelR/WIO/master/Listy/ListaZadan1.html
http://htmlpreview.github.io/?raw.githubusercontent.com/ZajdelR/WIO/master/Ćwiczenia/Wprowadzenie.html


Aby szybko pobrać plik:

<ul>
<li> <a class="download" href="https://github.com/ShareX/ShareX/releases/latest">Download</a>
<p class="release-info"></p>
<li><a href="https://raw.githubusercontent.com/ZajdelR/WIO/master/Ćwiczenia/Cwiczenie1.ipynb?raw=True" download="Cwiczenie1.ipynb" target="_blank">Jupyter Notebook: Cwiczenie1</a>
<li> <a href="/Ćwiczenia/Cwiczenie1.ipnyb" download>Jupyter Notebook: Cwiczenie1</a>
<li><a href="https://raw.githubusercontent.com/ZajdelR/WIO/master/Ćwiczenia/Cwiczenia2.ipynb?raw=True" download="Cwiczenie2.ipynb" target="_blank">Jupyter Notebook: Cwiczenie2</a>
  
<li><a href="www.google.com" download="google.html" target="_blank">Google</a>
</ul>
