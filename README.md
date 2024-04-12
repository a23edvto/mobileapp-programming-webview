I detta projekt har jag först och främst gjort en fork på det redan existerande projektet. Efter
det bytte jag namn på appen i "strings.xml". Efter detta slog jag på internetåtkomst för min app
genom att gå till AndroidManifest.xml och skrev:

<uses-permission android:name="android.permission.INTERNET"/>

Efter detta skapades ett WebView element i layoutfilen "activity_main.xml" samt att den redan
existerande "TextView" koden togs bort. Koden för WebView elementet ser ut såhär:

<WebView
android:id="@+id/my_webview"
android:layout_width="match_parent"
android:layout_height="match_parent" />

I koden finns även ett ID vid namn "@+id/my_webview", vilket lades till direkt efter. Sedan skapades
en WebView variabel vid namn "myWebView" som instantierades i "onCreate" och skrevs såhär:

myWebView=(WebView) findViewById(R.id.my_webview);
myWebView.setWebViewClient(new WebViewClient());

Efter detta lokaliserade jag WebView elementet med hjälp av Webview ID samt skapade en WebViewClient
som är bifogad till WebView. Efter detta slog jag på JavaScript i min WebViewClient:

WebSettings webSettings = myWebView.getSettings();
webSettings.setJavaScriptEnabled(true);

Sedan skapade jag en html sida och lade till den som en asset. Sen implementerade jag funktionerna
showExternalWebPage() och showInternalWebPage() genom att skriva varsin URL:

public void showExternalWebPage(){
    // TODO: Add your code for showing external web page here
    myWebView.loadUrl("https://google.se");
}

public void showInternalWebPage(){
    // TODO: Add your code for showing internal web page here
    myWebView.loadUrl("file:///android_asset/about.html");
}

I showInternalWebPage() länkade jag html filen. Tyvärr så funkade det inte att klicka på länken till
den externa webbsidan då det blev ett DNS fel där brandväggen blockerade som man kan se i bilden
nedan. Efter det kallade jag på de två funktionerna i "onOptionsItemSelected":

if (id == R.id.action_external_web) {
    Log.d("==>","Will display external web page");
    showExternalWebPage();
    return true;
}

if (id == R.id.action_internal_web) {
    Log.d("==>","Will display internal web page");
    showInternalWebPage();
    return true;
}



Bilder läggs i samma mapp som markdown-filen.

![](android.png)

Läs gärna:

- Boulos, M.N.K., Warren, J., Gong, J. & Yue, P. (2010) Web GIS in practice VIII: HTML5 and the canvas element for interactive online mapping. International journal of health geographics 9, 14. Shin, Y. &
- Wunsche, B.C. (2013) A smartphone-based golf simulation exercise game for supporting arthritis patients. 2013 28th International Conference of Image and Vision Computing New Zealand (IVCNZ), IEEE, pp. 459–464.
- Wohlin, C., Runeson, P., Höst, M., Ohlsson, M.C., Regnell, B., Wesslén, A. (2012) Experimentation in Software Engineering, Berlin, Heidelberg: Springer Berlin Heidelberg.
