---
title: Vytvářejte aplikace s nativním uživatelským rozhraním pomocí Xamarinu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 30f137e6-595d-4ce7-b8f5-415b07c1caa2
caps.latest.revision: 33
ms.author: crdun
manager: crdun
ms.openlocfilehash: 7a0284ab6b8d2e89e1c0129c2bc98fb486918f90
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297926"
---
# <a name="build-apps-with-native-ui-using-xamarin-in-visual-studio"></a>Vytváření aplikací s nativním uživatelským rozhraním pomocí Xamarinu v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Až provedete kroky v [nastavení a nainstalujete](../cross-platform/setup-and-install.md) a [ověříte své prostředí Xamarin](../cross-platform/verify-your-xamarin-environment.md), tento návod vám ukáže, jak vytvořit základní aplikaci Xamarin (zobrazenou níže) s NATIVNÍMI vrstvami uživatelského rozhraní. S nativním uživatelským rozhraním sdílený kód nachází v knihovně přenosných tříd (PCL) a jednotlivé platformy projekty obsahují definice uživatelského rozhraní.

 ![Aplikace Xamarin v Androidu a Windows Phone](../cross-platform/media/cross-plat-xamarin-build-1.png "Sestavení Xamarin pro více platy")

 Můžete udělat Tyhle věci na jejich vytváření:

- [Nastavení řešení](#solution)

- [Zápis kódu sdílené datové služby](#dataservice)

- [Návrh uživatelského rozhraní pro Android](#Android)

- [Návrh uživatelského rozhraní pro Windows Phone](#Windows)

- [Další postup](#next)

> [!TIP]
> Úplný zdrojový kód pro tento projekt najdete v [úložišti mobilní ukázky na GitHubu](https://github.com/xamarin/mobile-samples/tree/master/Weather).
>
> Pokud máte problémy nebo máte chyby, pošlete prosím otázky na [forums.Xamarin.com](https://forums.xamarin.com/). Mnoho chyb lze vyřešit aktualizací na nejnovější sady SDK, které vyžaduje Xamarin, které jsou popsány v [poznámkách k vydání verze Xamarin](https://developer.xamarin.com/) pro jednotlivé platformy.
>
> [!NOTE]
> Dokumentaci pro vývojáře Xamarinu pro několik kurzy rychlý start a podrobné informace o části nabízí také, jak je uvedeno níže. Na těchto stránkách Ujistěte se, že je v pravém horním rohu stránky zobrazíte návody pro Visual Studio specifické pro vybraná "Visual Studio".
>
> - Aplikace Xamarin s nativním uživatelským rozhraním:
>
>   - [Hello, Android](https://developer.xamarin.com/guides/android/getting_started/hello,android/) (jednoduchá aplikace s jednou obrazovkou)
>   - [Hello, Android s více obrazovkami](https://developer.xamarin.com/guides/android/getting_started/hello,android_multiscreen/) (aplikace s navigací mezi obrazovkami)
>   - [Návod k fragmentům Androidu](https://docs.microsoft.com/xamarin/android/platform/fragments/implementing-with-fragments/) (používá se pro obrazovky hlavní/podrobnosti, mimo jiné)
>   - [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
>   - [Hello, iOS s více obrazovkami](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS_multiscreen/)
>   - Aplikace Xamarin s Xamarin.Forms (sdílené uživatelské rozhraní)
>
>   - [Hello, Xamarin.Forms](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms/quickstart/)
>   - [Hello, Xamarin.Forms s více obrazovkami](https://developer.xamarin.com/guides/cross-platform/xamarin-forms/getting-started/hello-xamarin-forms-multiscreen/)

## <a name="solution"></a>Nastavení řešení
 Tyto kroky vytvoří řešení Xamarin s nativním uživatelským rozhraním, který obsahuje PCL pro sdílený kód a dva balíčky NuGet pro přidání.

1. V aplikaci Visual Studio vytvořte nové **prázdné řešení aplikace (nativní přenosné)** a pojmenujte ho **WeatherApp**. Tuto šablonu můžete snáze najít tak, že do vyhledávacího pole zadáte **nativní přenos** .

    Pokud tam není, možná budete muset nainstalovat Xamarin nebo povolit funkci sady Visual Studio 2015, přečtěte si téma [instalace a instalace](../cross-platform/setup-and-install.md).

2. Po kliknutí na tlačítko OK, abyste vytvořili řešení, budete mít několik jednotlivé projekty:

   - **WeatherApp (Portable)** : PCL, kde budete psát kód, který je sdílen napříč platformami, včetně běžné obchodní logiky a kódu uživatelského rozhraní pomocí Xamarin. Forms.

   - **WeatherApp. Droid**: projekt, který obsahuje nativní kód pro Android. To je nastaven jako výchozí projekt po spuštění.

   - **WeatherApp. iOS**: projekt, který obsahuje nativní kód iOS.

   - **WeatherApp. Winphone (Windows Phone 8,1)** : projekt obsahující nativní kód Windows Phone.

     V rámci každé nativní projektu mají přístup do nativní návrháře pro odpovídající platformu a můžete implementovat jednotlivých obrazovek platformy.

3. Přidejte balíček **Newtonsoft. JSON** a NuGet do projektu PCL, který budete používat ke zpracování informací získaných z datové služby počasí:

   - V Průzkumníku řešení klikněte pravým tlačítkem na **řešení ' WeatherApp '** a vyberte možnost **Spravovat balíčky NuGet pro řešení...** .

        V okně NuGet vyberte kartu **Procházet** a vyhledejte **Newtonsoft**.

   - Vyberte **Newtonsoft. JSON**.

   - Na pravé straně okna ověřte projekt **WeatherApp** (Jedná se o jediný projekt, ve kterém potřebujete balíček nainstalovat).

   - Zajistěte, aby se v poli **verze** nastavila **nejnovější stabilní** verze.

   - Klikněte na **Nainstalovat**.

   - ![Vyhledání a instalace balíčku NuGet Newtonsoft. JSON](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

4. Opakujte krok 3 a vyhledejte a nainstalujte balíček **Microsoft.NET. http** .

5. Sestavte řešení a ověřte, že zde nejsou žádné chyby buildu.

## <a name="dataservice"></a>Zápis kódu sdílené datové služby
 Projekt **WeatherApp (Portable)** je místo, kde budete psát kód pro přenosnou knihovnu tříd (PCL), která je sdílena napříč všemi platformami. PCL je automaticky zahrnut v balíčcích aplikace sestavené projekty zařízení s iOS, Android a Windows Phone.

 Takto přidejte kód PCL pro přístup a ukládání dat z této služby weather:

1. Pokud chcete tuto ukázku spustit, musíte si nejdřív zaregistrovat bezplatný klíč rozhraní API na [http://openweathermap.org/appid](https://openweathermap.org/appid).

2. Klikněte pravým tlačítkem na projekt **WeatherApp** a vyberte **Přidat > třídy...** V dialogovém okně **Přidat novou položku zadejte** název souboru **Weather.cs**. Tato třída budete používat k ukládání dat ze služby data o počasí.

3. Celý obsah **Weather.cs** nahraďte následujícím:

    ```csharp
    namespace WeatherApp
    {
        public class Weather
        {
            public string Title { get; set; }
            public string Temperature { get; set; }
            public string Wind { get; set; }
            public string Humidity { get; set; }
            public string Visibility { get; set; }
            public string Sunrise { get; set; }
            public string Sunset { get; set; }

            public Weather()
            {
                //Because labels bind to these values, set them to an empty string to
                //ensure that the label appears on all platforms by default.
                this.Title = " ";
                this.Temperature = " ";
                this.Wind = " ";
                this.Humidity = " ";
                this.Visibility = " ";
                this.Sunrise = " ";
                this.Sunset = " ";
            }
        }
    }
    ```

4. Přidejte další třídu do projektu PCL s názvem **DataService.cs** , ve kterém budete používat ke zpracování dat JSON z datové služby počasí.

5. Celý obsah **DataService.cs** nahraďte následujícím kódem:

    ```csharp
    using System.Threading.Tasks;
    using Newtonsoft.Json;
    using System.Net.Http;

    namespace WeatherApp
    {
        public class DataService
        {
            public static async Task<dynamic> getDataFromService(string queryString)
            {
                HttpClient client = new HttpClient();
                var response = await client.GetAsync(queryString);

                dynamic data = null;
                if (response != null)
                {
                    string json = response.Content.ReadAsStringAsync().Result;
                    data = JsonConvert.DeserializeObject(json);
                }

                return data;
            }
        }
    }
    ```

6. Přidejte třetí třídu do PCL s názvem **Core** , kde vložíte sdílenou obchodní logiku, jako je například logika, která vytvoří řetězec dotazu s PSČ, zavolá datovou službu počasí a naplní instanci třídy **počasí** .

7. Nahraďte obsah **Core.cs** následujícím způsobem:

    ```csharp
    using System;
    using System.Threading.Tasks;

    namespace WeatherApp
    {
        public class Core
        {
            public static async Task<Weather> GetWeather(string zipCode)
            {
                //Sign up for a free API key at http://openweathermap.org/appid
                string key = "YOUR KEY HERE";
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="
                    + zipCode + ",us&appid=" + key + "&units=imperial";

                //Make sure developers running this sample replaced the API key
                if (key == "YOUR API KEY HERE")
                {
                    throw new ArgumentException("You must obtain an API key from openweathermap.org/appid and save it in the 'key' variable.");
                }

                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);

                if (results["weather"] != null)
                {
                    Weather weather = new Weather();
                    weather.Title = (string)results["name"];
                    weather.Temperature = (string)results["main"]["temp"] + " F";
                    weather.Wind = (string)results["wind"]["speed"] + " mph";
                    weather.Humidity = (string)results["main"]["humidity"] + " %";
                    weather.Visibility = (string)results["weather"][0]["main"];

                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);
                    weather.Sunrise = sunrise.ToString() + " UTC";
                    weather.Sunset = sunset.ToString() + " UTC";
                    return weather;
                }
                else
                {
                    return null;
                }
            }
        }
    }
    ```

8. Místo *v kódu nahraďte* klíč rozhraní API, který jste získali v kroku 1 (stále k tomu potřebují uvozovky).

9. MyClass.cs v PCL odstraňte, protože nebudeme používat ho.

10. Sestavte projekt PCL **WeatherApp** , abyste se ujistili, že kód je správný.

## <a name="Android"></a>Návrh uživatelského rozhraní pro Android
 Teď jsme budete návrh uživatelského rozhraní, připojte ho ke sdílenému kódu a pak spusťte aplikaci.

### <a name="design-the-look-and-feel-of-your-app"></a>Navrhnout vzhled a chování vaší aplikace

1. V **Průzkumník řešení**rozbalte **WeatherApp. Droid**>**prostředky**>složku **rozložení** a otevřete **Main. axml**. Tím se otevře soubor v vizuálního návrháře. (Pokud se zobrazí chyba související s jazykem Java, přečtěte si tento [Blogový příspěvek](https://forums.xamarin.com/discussion/32365/connection-to-the-layout-renderer-failed-in-xs-5-7-and-xamarinvs-3-9).)

    > [!TIP]
    > V projektu je mnoho dalších souborů. Prozkoumávání je nad rámec tohoto tématu, ale pokud se chcete podrobně do struktury projektu pro Android a trochu více, podívejte se na [část 2 hlubokou podrobně](https://docs.microsoft.com/xamarin/android/get-started/hello-android/hello-android-deepdive?pivots=windows) tématu Hello pro android na Xamarin.com.

2. Vyberte a odstraňte výchozí tlačítko, které se zobrazí v návrháři.

3. Otevřete sadu nástrojů pomocí **zobrazení > jiné sady nástrojů > pro Windows**.

4. Z **panelu nástrojů**přetáhněte ovládací prvek **RelativeLayout** do návrháře. Tento ovládací prvek budete používat jako nadřazený kontejner pro ostatní ovládací prvky.

    > [!TIP]
    > Pokud se nezdá, že rozložení vypadá správně, uložte soubor a přepíná mezi kartami **design** a **source** , které se mají aktualizovat.

5. V okně **vlastnosti** nastavte vlastnost **Background** (ve skupině styl) na `#545454`.

6. Z **panelu nástrojů**přetáhněte ovládací prvek **TextView** do ovládacího prvku **RelativeLayout** .

7. V okně **vlastnosti** nastavte tyto vlastnosti (Poznámka: pomocí tlačítka seřadit na panelu nástrojů okno Vlastnosti může pomoci seznam seřadit podle abecedy):

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**textové**|**Hledat podle PSČ**|
    |**id**|`@+id/ZipCodeSearchLabel`|
    |**layout_marginLeft**|`10dp`|
    |**textColor**|`@android:color/white`|
    |**Vytvořil systém**|`bold`|

    > [!TIP]
    > Všimněte si, že mnoho vlastností neobsahují rozevírací seznam hodnot, které můžete vybrat.  Může být obtížné odhadnout jaké řetězcovou hodnotu pro jakékoli dané vlastnosti. U návrhů zkuste vyhledat název vlastnosti na stránce třídy [R. attr](https://developer.android.com/reference/android/R.attr.html) .
    >
    >  Rychlé vyhledávání na webu často vede na stránku na [http://stackoverflow.com/](https://stackoverflow.com/) , kde ostatní používali stejnou vlastnost.

     Pro referenci, pokud přepnete do zobrazení **zdroje** , měl by se zobrazit následující kód pro tento element:

    ```xml
    <TextView
        android:text="Search by Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/ZipCodeSearchLabel"
        android:layout_centerVertical="true"
        android:layout_marginLeft="10dp"
        android:textColor="@android:color/white"
        android:textStyle="bold" />

    ```

8. Z **panelu nástrojů**přetáhněte ovládací prvek **TextView** do ovládacího prvku **RelativeLayout** a umístěte jej pod ovládací prvek ZipCodeSearchLabel. To provedete přetažením na příslušný okraji existujícího ovládacího prvku; nový ovládací prvek pomáhá přiblížení má Návrhář trochu to.

9. V okně **vlastnosti** nastavte tyto vlastnosti:

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**textové**|**PSČ**|
    |**id**|`@+id/ZipCodeLabel`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginTop**|`5dp`|

     Kód v zobrazení **zdroj** by měl vypadat takto:

    ```xml
    <TextView
        android:text="Zip Code"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeSearchLabel"
        android:id="@+id/ZipCodeLabel"
        android:layout_marginTop="5dp"
        android:layout_marginLeft="10dp" />
    ```

10. Z **panelu nástrojů**přetáhněte ovládací prvek **číslo** na **RelativeLayout**, umístěte ho pod popisek **PSČ** . Potom nastavte následující vlastnosti:

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**id**|`@+id/zipCodeEntry`|
    |**layout_marginLeft**|`10dp`|
    |**layout_marginBottom**|`10dp`|
    |**Délk**|`165dp`|

     Znovu kód:

    ```xml
    <EditText
        android:inputType="number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/ZipCodeLabel"
        android:id="@+id/zipCodeEntry"
        android:layout_marginLeft="10dp"
        android:layout_marginBottom="10dp"
        android:width="165dp" />
    ```

11. Z **panelu nástrojů**přetáhněte **tlačítko** do ovládacího prvku **RelativeLayout** a umístěte jej napravo od ovládacího prvku zipCodeEntry. Nastavte tyto vlastnosti:

    |Vlastnost|Hodnota|
    |--------------|-----------|
    |**id**|`@+id/weatherBtn`|
    |**textové**|**Získat počasí**|
    |**layout_marginLeft**|`20dp`|
    |**layout_alignBottom**|`@id/zipCodeEntry`|
    |**Délk**|`165dp`|

    ```xml
    <Button    android:text="Get Weather"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_toRightOf="@id/zipCodeEntry"
        android:id="@+id/weatherBtn"
        android:layout_marginLeft="20dp"
        android:layout_alignBottom="@id/zipCodeEntry"
        android:width="165dp" />
    ```

12. Nyní máte dostatek zkušeností k sestavení základní uživatelské rozhraní pomocí návrháře pro Android. Můžete také vytvořit uživatelské rozhraní přidáním kódu přímo do souboru .asxml stránky. Chcete-li vytvořit zbytek uživatelského rozhraní tímto způsobem, přepněte do zobrazení zdroje v návrháři a potom za následující značku *pod* značkou `</RelativeLayout>` (Ano, to je pod značkou... Tyto prvky nejsou obsaženy v ReleativeLayout).

    ```xml
    <TextView
            android:text="Location"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationLabel"
            android:layout_marginLeft="10dp"
            android:layout_marginTop="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/locationText"
            android:layout_marginLeft="20dp"
            android:layout_marginBottom="10dp" />
        <TextView
            android:text="Temperature"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/tempText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Wind Speed"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/windText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Humidity"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidtyLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/humidityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Visibility"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/visibilityText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunrise"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunriseText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />
        <TextView
            android:text="Time of Sunset"
            android:textAppearance="?android:attr/textAppearanceSmall"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetLabel"
            android:layout_marginLeft="10dp" />
        <TextView
            android:textAppearance="?android:attr/textAppearanceMedium"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/sunsetText"
            android:layout_marginBottom="10dp"
            android:layout_marginLeft="20dp" />

    ```

13. Uložte soubor a přepněte se do zobrazení **Návrh** . Vaše uživatelské rozhraní by měl vypadat takto:

     ![Uživatelské rozhraní pro aplikaci pro Android](../cross-platform/media/xamarin-androidui.png "Xamarin_AndroidUI")

14. Otevřete **MainActivity.cs** a odstraňte řádky v metodě *Create* , které odkazují na výchozí tlačítko, které bylo dříve odebráno. Až to budete mít, kód by měl vypadat takto:

    ```
    protected override void OnCreate (Bundle bundle)
    {
        base.OnCreate (bundle);

        // Set our view from the "main" layout resource
        SetContentView (Resource.Layout.Main);
    }
    ```

15. Vytvoření projektu pro Android ke kontrole vaší práce. Všimněte si, že při sestavování se do souboru **Resource.Designer.cs** přidá ID ovládacích prvků, takže můžete odkazovat na ovládací prvky podle názvu v kódu.

### <a name="consume-your-shared-code"></a>Používat sdílený kód

1. V editoru kódu otevřete soubor **MainActivity.cs** projektu **WeatherApp** a nahraďte jeho obsah následujícím kódem. Tento kód volá metodu `GetWeather`, kterou jste definovali ve svém sdíleném kódu. Poté v Uživatelském rozhraní aplikace zobrazuje data, která je načten z metody.

    ```csharp
    using System;
    using Android.App;
    using Android.Widget;
    using Android.OS;

    namespace WeatherApp.Droid
    {
        [Activity(Label = "Sample Weather App", MainLauncher = true, Icon = "@drawable/icon")]
        public class MainActivity : Activity
        {
            protected override void OnCreate(Bundle bundle)
            {
                base.OnCreate(bundle);

                SetContentView(Resource.Layout.Main);

                Button button = FindViewById<Button>(Resource.Id.weatherBtn);

                button.Click += Button_Click;
            }

            private async void Button_Click(object sender, EventArgs e)
            {
                EditText zipCodeEntry = FindViewById<EditText>(Resource.Id.zipCodeEntry);

                if (!String.IsNullOrEmpty(zipCodeEntry.Text))
                {
                    Weather weather = await Core.GetWeather(zipCodeEntry.Text);
                    FindViewById<TextView>(Resource.Id.locationText).Text = weather.Title;
                    FindViewById<TextView>(Resource.Id.tempText).Text = weather.Temperature;
                    FindViewById<TextView>(Resource.Id.windText).Text = weather.Wind;
                    FindViewById<TextView>(Resource.Id.visibilityText).Text = weather.Visibility;
                    FindViewById<TextView>(Resource.Id.humidityText).Text = weather.Humidity;
                    FindViewById<TextView>(Resource.Id.sunriseText).Text = weather.Sunrise;
                    FindViewById<TextView>(Resource.Id.sunsetText).Text = weather.Sunset;
                }
            }
        }
    }
    ```

### <a name="run-the-app-and-see-how-it-looks"></a>Spusťte aplikaci a zjistit, jak to funguje

1. V **Průzkumník řešení**zajistěte, aby byl projekt **WeatherApp. Droid** nastaven jako spouštěný projekt.

2. Vyberte příslušné zařízení nebo emulátoru cílové a pak spusťte aplikaci stisknutím klávesy F5.

3. V zařízení nebo v emulátoru zadejte do pole pro úpravy platné USA PSČ (například: 60601) a stiskněte tlačítko **získat počasí**. Data o počasí v dané oblasti se pak objeví v ovládacích prvcích.

     ![Aplikace počasí pro Android a Windows Phone](../cross-platform/media/xamarin-getstarted-results.png "Xamarin_GetStarted_Results")

> [!TIP]
> Úplný zdrojový kód tohoto projektu je v [úložišti mobilní vzorky na GitHubu](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="Windows"></a>Návrh uživatelského rozhraní pro Windows Phone
 Nyní jsme budete návrh uživatelského rozhraní pro Windows Phone, připojte ho ke sdílenému kódu a pak spusťte aplikaci.

### <a name="design-the-look-and-feel-of-your-app"></a>Navrhnout vzhled a chování vaší aplikace
 Proces navrhování nativních uživatelských rozhraní Windows Phone v aplikaci Xamarin se nijak neliší od jiných nativní aplikace pro Windows Phone. Z tohoto důvodu nebude přejdeme k podrobnostem tady, jak používat návrháře. Pro tento postup si přečtěte téma [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

 Místo toho jednoduše otevřete MainPage.xaml a nahraďte celý kód XAML následujícím kódem:

```xaml
<Page
    x:Class="WeatherApp.WinPhone.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:WeatherApp.WinPhone"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">

    <Grid>
        <StackPanel HorizontalAlignment="Left" Height="40" Margin="10,0,0,0" VerticalAlignment="Top" Width="400">
            <TextBlock x:Name="pageTitle" Text="Weather App" FontSize="30" />
        </StackPanel>
        <StackPanel HorizontalAlignment="Left" Height="120" Margin="10,40,0,0" VerticalAlignment="Top" Width="400" Background="#FF545454">

            <TextBlock x:Name="zipCodeSearchLabel" TextWrapping="Wrap" Text="Search by Zip Code" FontSize="18" FontWeight="Bold" HorizontalAlignment="Left" Margin="10,10,0,0"/>
            <TextBlock x:Name="zipCodeLabel" TextWrapping="Wrap" Text="Zip Code" Margin="10,5,0,0" FontSize="14" Foreground="#FFA8A8A8"/>
            <StackPanel Orientation="Horizontal">
                <TextBox x:Name="zipCodeEntry" Margin="10,10,0,0" Text="" VerticalAlignment="Top" InputScope="Number" Width="165" />
                <Button x:Name="weatherBtn" Content="Get Weather" Width="165" Margin="20,0,0,0" Height="60" Click="GetWeatherButton_Click"/>
            </StackPanel>
        </StackPanel>
        <StackPanel Margin="10,175,0,0">
            <TextBlock x:Name="locationLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Location" VerticalAlignment="Top"/>
            <TextBlock x:Name="locationText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="tempText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="windLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Wind Speed" VerticalAlignment="Top"/>
            <TextBlock x:Name="windText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Humidity" VerticalAlignment="Top"/>
            <TextBlock x:Name="humidityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Temperature" VerticalAlignment="Top"/>
            <TextBlock x:Name="visibilityText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunriweatherse" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunriseText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetLabel" HorizontalAlignment="Left" FontSize="14" Foreground="#FFA8A8A8" TextWrapping="Wrap" Text="Time of Sunset" VerticalAlignment="Top"/>
            <TextBlock x:Name="sunsetText" Margin="10,0,0,10" HorizontalAlignment="Left" FontSize="18" TextWrapping="Wrap" VerticalAlignment="Top"/>
        </StackPanel>
    </Grid>
</Page>
```

 V návrhovém zobrazení by měla vaše uživatelské rozhraní vypadat takto:

 ![Windows Phone uživatelské rozhraní aplikace](../cross-platform/media/xamarin-winphone-finalui.png "Xamarin_WinPhone_FinalUI")

### <a name="consume-your-shared-code"></a>Používat sdílený kód

1. V návrháři vyberte tlačítko **získat počasí** .

2. V okně **vlastnosti** klikněte na tlačítko obslužná rutina události (![ikona obslužné rutiny událostí sady Visual Studio](../cross-platform/media/blend-vs-eventhandlers-icon.png "blend_VS_EventHandlers_icon")).

     Tato ikona se zobrazí v horním rohu okna **vlastnosti** .

3. Vedle události **Click** zadejte **GetWeatherButton_Click**a potom stiskněte klávesu ENTER.

     Tím se vygeneruje obslužná rutina události s názvem `GetWeatherButton_Click`. Otevře editor kódu a umístí kurzor uvnitř bloku kódu obslužné rutiny události.  Poznámka: Pokud editor neotevře při stisknutí klávesy ENTER, stačí dvakrát klikněte na název události.

4. Tato obslužná rutina události nahraďte následujícím kódem.

    ```csharp
    private async void GetWeatherButton_Click(object sender, RoutedEventArgs e)
    {
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))
        {
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);
            locationText.Text = weather.Title;
            tempText.Text = weather.Temperature;
            windText.Text = weather.Wind;
            visibilityText.Text = weather.Visibility;
            humidityText.Text = weather.Humidity;
            sunriseText.Text = weather.Sunrise;
            sunsetText.Text = weather.Sunset;

            weatherBtn.Content = "Search Again";
        }
    }
    ```

     Tento kód volá metodu `GetWeather`, kterou jste definovali ve svém sdíleném kódu. Toto je stejnou metodu, která je volána v aplikaci pro Android. Tento kód také ukazuje dat načtených z této metody v ovládacích prvcích uživatelského rozhraní aplikace.

5. V MainPage.xaml.cs, který je otevřen, odstraňte veškerý kód v rámci metody **OnNavigatedTo** . Tento kód jednoduše zpracovat výchozí tlačítko, které se odstranily při jsme nahradili obsah souboru mainpage.XAML.

### <a name="run-the-app-and-see-how-it-looks"></a>Spusťte aplikaci a zjistit, jak to funguje

1. V **Průzkumník řešení**nastavte projekt **WeatherApp. Winphone** jako spouštěný projekt.

2. Stisknutím klávesy F5 spusťte aplikaci.

3. V emulátoru Windows Phone zadejte do pole pro úpravy platný kód USA zip (například: 60601) a stiskněte tlačítko **získat počasí**. Data o počasí v dané oblasti se pak objeví v ovládacích prvcích.

     ![Verze spuštěné aplikace ve Windows](../cross-platform/media/xamarin-getstarted-results-windows.png "Xamarin_GetStarted_Results_Windows")

> [!TIP]
> Úplný zdrojový kód tohoto projektu je v [úložišti mobilní vzorky na GitHubu](https://github.com/xamarin/mobile-samples/tree/master/Weather).

## <a name="next"></a>Další kroky
 **Přidání uživatelského rozhraní pro iOS do řešení**

 Tuto ukázku rozšiřte přidáním nativní uživatelské rozhraní pro iOS. To bude potřeba připojit k počítači Mac ve vaší místní síti, která má Xcode a Xamarin nainstalovat. Až to uděláte, můžete použít Návrháře iOS přímo v sadě Visual Studio. Dokončenou aplikaci najdete v [úložišti Mobile Samples na GitHubu](https://github.com/xamarin/mobile-samples/tree/master/Weather) .

 Přečtěte si také návod [Hello, iOS](https://docs.microsoft.com/xamarin/ios/get-started/hello-ios/hello-ios-quickstart?pivots=windows) (Xamarin.com). Všimněte si, že na této stránce si být jisti, že "Visual Studio" je vybrat v pravém horním rohu stránky na xamarin.com tak, aby správnou sadu pokynů.

 **Přidat kód specifický pro platformu do sdíleného projektu**

 Sdílený kód v PCL je nezávislá na platformě, vzhledem k tomu, PCL kompiluje jednou a součástí každý balíček aplikace pro konkrétní platformu. Pokud chcete napsat sdílený kód, který používá Podmíněná kompilace k izolaci kódu specifického pro platformu, můžete použít *sdílený* projekt. Další podrobnosti najdete v tématu [možnosti sdílení](https://docs.microsoft.com/xamarin/cross-platform/app-fundamentals/code-sharing) po Xamarin.com.

## <a name="see-also"></a>Viz také
 [Web Xamarin Developer web](https://docs.microsoft.com/xamarin/) [Windows Dev Center](https://dev.windows.com/en-us) [SWIFT C# a rychlý referenční plakát](https://aka.ms/scposter)
