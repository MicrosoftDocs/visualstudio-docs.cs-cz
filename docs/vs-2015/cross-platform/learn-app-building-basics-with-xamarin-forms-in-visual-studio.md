---
title: Základy vytváření aplikací s Xamarin.Forms
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 0cbc20bd714cabf9747145c114abfaa58a2e52a6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058321"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Základy vytváření aplikací s Xamarin.Forms v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Jakmile jste udělali kroky [nastavení a instalaci](../cross-platform/setup-and-install.md) a [ověření prostředí Xamarinu](../cross-platform/verify-your-xamarin-environment.md), tento návod ukazuje, jak vytvořit základní aplikaci (viz dole) s Xamarin.Forms. Pomocí Xamarin.Forms napíšete všech kódů uživatelského rozhraní jednou v knihovně přenosných tříd (PCL). Xamarin se pak automaticky generují nativní ovládací prvky uživatelského rozhraní pro iOS, Android a Windows platformy. Doporučujeme tento přístup, protože PCL možnost nejlépe podporuje používání pouze rozhraní .NET API, které jsou podporovány v rámci všechny cílové platformy a vzhledem k tomu, že Xamarin.Forms umožňuje sdílet uživatelské rozhraní kódu napříč platformami.

 ![Ukázka aplikace počasí na Android, iOS a Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

 Můžete udělat Tyhle věci na jejich vytváření:

-   [Nastavení řešení](#solution)

-   [Zápis kódu služby sdílená data](#dataservice)

-   [Začněte psát sdíleným kódem uživatelského rozhraní](#uicode)

-   [Testování aplikace pomocí emulátoru Visual Studia pro Android](#test)

-   [Dokončení uživatelského rozhraní pomocí přirozený vzhled a chování napříč platformami](#finish)

> [!TIP]
>  Najdete kompletní zdrojový kód pro tento projekt v [ukázky xamarin forms úložišti na Githubu](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

##  <a name="solution"></a> Nastavení řešení
 Tyto kroky vytvoří řešení Xamarin.Forms, která obsahuje PCL pro sdílený kód a dva balíčky NuGet pro přidání.

1.  V sadě Visual Studio vytvořte nový **prázdná aplikace (Xamarin.Forms přenosná)** řešení a pojmenujte ho **WeatherApp**. Tuto šablonu lze najít nejsnadněji tak, že zadáte **Xamarin.Forms** do vyhledávacího pole.

     Pokud tam není, bude pravděpodobně nutné nainstalujte si Xamarin, nebo povolte funkce sady Visual Studio 2015, najdete v článku [nastavení a instalaci](../cross-platform/setup-and-install.md).

     ![Vytvoření nové prázdné aplikace &#40;Xamarin.Forms Portable&#41; projektu](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  Po kliknutí na tlačítko OK, abyste vytvořili řešení, budete mít několik jednotlivé projekty:

    -   **WeatherApp (Portable)**: PCL, kde budete psát kód, který je sdílen napříč platformami, včetně běžné obchodní logiky a kód uživatelského rozhraní pomocí Xamarin.Forms.

    -   **WeatherApp.Droid**: projekt obsahující kód nativní Android. To je nastaven jako výchozí projekt po spuštění.

    -   **WeatherApp.iOS**: projekt obsahující kód nativní aplikace pro iOS.

    -   **WeatherApp.UWP**: projekt, který obsahuje Windows 10 UPW kódu.

    -   **WeatherApp.Windows (Windows 8.1)**: projekt obsahující nativní kód pro Windows 8.1.

    -   **WeatherApp.WinPhone (Windows Phone 8.1)**: projekt obsahující nativní kód Windows Phone.

    > [!NOTE]
    >  Můžete odstranit kterýkoli z projektů pro platformu, která nejsou cílení zdarma. Pro účely tohoto návodu jsme budete odkazovat projekty Android, iOS a Windows Phone 8.1. Práce s UWP a Windows 8.1 projekty je velmi podobně jako při práci s projektem Windows Phone 8.1.

     V rámci každé nativní projektu mají přístup do nativní návrháře pro odpovídající platformu a můžete implementovat platformy jednotlivých obrazovek a funkčnosti podle potřeby.

3.  Upgradujte balíček Xamarin.Forms NuGet v rámci vašeho řešení na nejnovější stabilní verzi následujícím způsobem. Doporučujeme, abyste to pokaždé, když vytvoříte nové řešení Xamarin:

    -   Vyberte **nástroje > Správce balíčků NuGet > spravovat balíčky NuGet pro řešení**.

    -   V části **aktualizace** kartě **Xamarin.Forms** aktualizovat a zaškrtněte, pokud chcete aktualizovat všechny projekty v řešení. (Poznámka: nechat žádné aktualizace pro Xamarin.Android.Support nezaškrtnutou.)

    -   Aktualizace **verze** pole **poslední stabilní** verzi, která je k dispozici.

    -   Klikněte na tlačítko **aktualizace**.

         ![Aktualizuje se balíček Xamarin.Forms NuGet](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

4.  Přidat **Newtonsoft.Json** a balíček NuGet do projektu PCL, které budete používat ke zpracování informace načtenými z datové služby weather:

    -   Ve správci balíčků NuGet (stále otevřen v kroku 3), vyberte **Procházet** kartu a vyhledejte **Newtonsoft**.

    -   Vyberte **Newtonsoft.Json**.

    -   Zkontrolujte, **WeatherApp** projektu (jedná se o pouze projekt, ve které je potřeba nainstalovat balíček).

    -   Zkontrolujte **verze** pole se nastaví **nejnovější stabilní verze** verze.

    -   Klikněte na tlačítko **nainstalovat**.

    -   ![Vyhledání a instalace balíčku Newtonsoft.Json NuGet](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

5.  Opakujte krok 4 najít a nainstalovat **Microsoft.Net.Http** balíčku.

6.  Sestavte řešení a ověřte, že zde nejsou žádné chyby buildu.

##  <a name="dataservice"></a> Zápis kódu služby sdílená data
 **WeatherApp (Portable)** projektu je, kde budete psát kód pro přenosné knihovny tříd (PCL), jež jsou sdílena mezi všemi platformami. V aplikaci je automaticky zahrnut PCL balíčky sestavení zařízení s iOS, Android a Windows Phone projektů.

 Ke spuštění této ukázky je nutné nejdřív zaregistrovat bezplatný klíč rozhraní API v [ http://openweathermap.org/appid ](http://openweathermap.org/appid).

 Takto přidejte pak kód PCL pro přístup a ukládání dat z této služby weather:

1.  Klikněte pravým tlačítkem myši **WeatherApp** projektu a vyberte **Přidat > třída...** . V **přidat novou položku** dialogového okna, název souboru **Weather.cs**. Tato třída budete používat k ukládání dat ze služby data o počasí.

2.  Nahradí celý obsah **Weather.cs** následujícím kódem:

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

3.  Přidejte jinou třídu do projektu PCL s názvem **DataService.cs** ve které budete používat ke zpracování dat JSON z datové služby počasí.

4.  Nahradí celý obsah **DataService.cs** následujícím kódem:

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

5.  Přidejte třídu třetí PCL s názvem **Core** místo, kam budete dáte sdílené obchodní logiku, jako jsou logiku, která tvoří řetězec dotazu s PSČ, volá službu data o počasí a naplní instance **počasí**třídy.

6.  Nahraďte obsah **Core.cs** následujícím kódem:

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

7.  Sestavení **WeatherApp** projekt PCL, abyste měli jistotu, kód je správný.

##  <a name="uicode"></a> Začněte psát sdíleným kódem uživatelského rozhraní
 Xamarin.Forms umožňuje implementovat v PCL sdíleným kódem uživatelského rozhraní. V tomto postupu přidáte obrazovku PCL s tlačítkem, jeho textu pomocí dat vrácených dat o počasí aktualizace služby kód přidaný v předchozí části:

1.  Přidat **Forms Xaml Page** s názvem **WeatherPage.cs** kliknutím pravým tlačítkem myši **WeatherApp** projekt a výběrem **Přidat > Nová položka...** . V **přidat novou položku** dialogové okno hledání na "Formulářů," vyberte **Forms Xaml Page**a pojmenujte ho **WeatherPage.cs**.

     Xamarin.Forms je založené na XAML, takže tento krok vytvoří **WeatherPage.xaml** soubor spolu se souborem vnořeného kódu **WeatherPage.xaml.cs**. To umožňuje generování uživatelského rozhraní XAML nebo kódu. Část v tomto názorném postupu budete používat.

     ![Přidání nové stránky XAML Xamarin.Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

2.  Chcete-li přidat tlačítka na obrazovku WeatherPage, nahraďte obsah WeatherPage.xaml následujícími způsoby:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     Všimněte si, že název tlačítka musí být definován pomocí **x: Name** atribut tak, aby toto tlačítko můžete odkazovat pomocí názvu z v rámci souboru kódu na pozadí.

3.  Chcete-li přidat obslužnou rutinu události pro tlačítka **kliknutí na** událost aktualizace textu tlačítka, nahraďte obsah **WeatherPage.xaml.cs** níže uvedeného kódu. (Můžete změnit na jiný kód zip "60601".)

    ```csharp
    using System;
    using Xamarin.Forms;

    namespace WeatherApp
    {
        public partial class WeatherPage: ContentPage
        {
            public WeatherPage()
            {
                InitializeComponent();
                this.Title = "Sample Weather App";
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;

                //Set the default binding to a default object for now
                this.BindingContext = new Weather();
            }

            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
            {
                Weather weather = await Core.GetWeather("60601");
                getWeatherBtn.Text = weather.Title;
            }
        }
    }
    ```

4.  Chcete-li otevřít **WeatherPage** jako první obrazovku při spuštění aplikace nahradí výchozí konstruktor v **App.cs** následujícím kódem:

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5.  Sestavte projekt WeatherApp PCL a ujistěte se, že kód je správný.

##  <a name="test"></a> Testování aplikace pomocí emulátoru Visual Studia pro Android
 Nyní jste připraveni aplikaci spustit! Můžeme spustit jenom verze Androidu nyní chcete ověřit, že aplikace je získání dat ze služby počasí. Později je potřeba taky spustit na iOS a Windows Phone verze po přidání další prvky uživatelského rozhraní. (Poznámka: Pokud používáte Visual Studio ve Windows 7, budeme postupujte stejným způsobem, ale místo toho se Xamarin Playeru.)

1.  Nastavte **WeatherApp.Droid** projekt jako spouštěný projekt tak, že pravým tlačítkem myši a vyberete **nastavit jako spouštěný projekt**.

2.  Na panelu nástrojů sady Visual Studio, zobrazí se vám **WeatherApp.Droid** uvedené jako cílový projekt. Vyberte jednu z emulátorů Androidu pro ladění a spuštění **F5**. Doporučujeme použít jeden z **emulátoru VS** možnosti, které se spustí aplikaci v emulátoru Visual Studia pro Android možnosti.

     ![Výběr cíle ladění emulátoru VS](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

3.  Při spuštění aplikace se spustila v emulátoru, klikněte na tlačítko **získat počasí** tlačítko. Byste měli vidět text na tlačítko Aktualizovat, aby **Chicago, IL**, což je *název* vlastnost dat načtených z této služby počasí.

     ![Informace o počasí aplikace před a po klepnutí na tlačítko](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

##  <a name="finish"></a> Dokončení uživatelského rozhraní pomocí přirozený vzhled a chování napříč platformami
 Xamarin.Forms vykreslí nativní ovládací prvky uživatelského rozhraní pro každou platformu, aby vaše aplikace automaticky nemá přirozený vzhled a chování. Tento údaj zobrazíte více jasně, Pojďme dokončení uživatelského rozhraní pomocí vstupního pole pro PSČ a pak zobrazí data o počasí, která je vrácena ze služby.

1. Nahraďte obsah **WeatherPage.xaml** s následujícím kódem. Všimněte si, že každý prvek má název, pomocí **x: Name** atributu, jak je popsáno výše, aby element může odkazovat z kódu. Xamarin.Forms také nabízí celou řadu [možnosti rozložení](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com); tady, používá WeatherPage [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).

   ```xaml
   <?xml version="1.0" encoding="utf-8" ?>
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
          x:Class="WeatherApp.WeatherPage">

     <ContentPage.Resources>
       <ResourceDictionary>
         <Style x:Key="labelStyle" TargetType="Label">
           <Setter Property="TextColor" Value="#a8a8a8" />
           <Setter Property="FontSize" Value="Small" />
         </Style>
         <Style x:Key="fieldStyle" TargetType="Label">
           <Setter Property="TextColor">
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />
           </Setter>
           <Setter Property="FontSize" Value="Medium" />
         </Style>
         <Style x:Key="fieldView" TargetType="ContentView">
           <Setter Property="Padding" Value="10,0,0,0" />
         </Style>
       </ResourceDictionary>
     </ContentPage.Resources>

     <ContentPage.Content>
       <ScrollView>
         <StackLayout>
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"
                 BackgroundColor="#545454">
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"
                   FontSize="Medium" />
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />
               <Entry x:Name="zipCodeEntry" />
             </StackLayout>
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >
                 <!-- Set iOS colors; use defaults on other platforms -->
                 <Button.TextColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.TextColor>
                 <Button.BorderColor>
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>
                 </Button.BorderColor>
               </Button>
             </StackLayout>
           </StackLayout>
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
             <Label Text="Location" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="tempLabel" Text="{Binding Temperature}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
             <ContentView Style="{StaticResource fieldView}">
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"
                   Style="{StaticResource fieldStyle}" />
             </ContentView>
           </StackLayout>
         </StackLayout>
       </ScrollView>
     </ContentPage.Content>
   </ContentPage>
   ```

    Všimněte si, **OnPlatform** značky v Xamarin.Forms. **OnPlatform** vybere hodnotu vlastnosti, která je specifická pro aktuální platformu, na kterém běží aplikace (viz [externí syntaxe XAML](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) (xamarin.com). Tady používáme nastavit různé barvy pro datová pole: bílá na zařízení s Androidem a Windows Phone, Black v systému iOS. Můžete použít **OnPlatform** pro všechny vlastnosti a všechny datové typy s úpravami specifické pro platformu kdekoli ve vaší XAML. V souboru kódu na pozadí, můžete použít [Device.OnPlatform API](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) ke stejnému účelu.

2. V **WeatherPage.xaml.cs**, nahraďte **GetWeatherBtn_Clicked** obslužné rutiny události pomocí kódu níže. Tento kód ověří, že je PSČ polem pro zadání, načte data pro tento kód zip, nastaví kontext vazby celou obrazovku na výsledný instanci počasí a pak nastaví text tlačítka na "Vyhledávání znovu." Všimněte si, že každému popisku v uživatelském rozhraní vytvoří vazbu na vlastnost třídy počasí, tak při nastavíte, kontextu vazby na obrazovce a **počasí** instance, tyto popisky automaticky aktualizovat.

   ```csharp
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)
   {
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))
       {
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);
           this.BindingContext = weather;
           getWeatherBtn.Text = "Search Again";
       }
   }
   ```

3. Spuštění aplikace na všech třech platformách – Android, iOS a Windows Phone – pravým tlačítkem myši na příslušný projekt, výběrem sady jako projekt po spuštění a spuštění aplikace na zařízení nebo emulátor nebo simulátor. Zadejte platné PSČ USA (například 60601) a stiskněte tlačítko získat počasí a zobrazte data o počasí v dané oblasti, jak je znázorněno níže. Samozřejmě musíte mít Visual Studio připojená k počítači Mac OS X ve vaší síti pro projekt pro iOS.

    ![Ukázka aplikace počasí na Android, iOS a Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

   Úplný zdrojový kód pro tento projekt je v [ukázky xamarin forms úložišti na Githubu](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
