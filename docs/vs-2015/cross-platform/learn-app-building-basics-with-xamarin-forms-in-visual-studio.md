---
title: Seznámení se základy vytváření aplikací pomocí Xamarin. Forms
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 09da3bd59163cbef8b33b1d5ece732330e32eac7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918934"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Základy vytváření aplikací s Xamarin.Forms v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Až provedete kroky v tématu [nastavení a nainstalujete](../cross-platform/setup-and-install.md) a [ověříte své prostředí Xamarin](../cross-platform/verify-your-xamarin-environment.md), tento návod vám ukáže, jak vytvořit základní aplikaci (zobrazenou níže) pomocí Xamarin. Forms. Pomocí Xamarin. Forms napíšete celý kód uživatelského rozhraní jednou v přenositelné knihovně tříd (PCL). Xamarin pak automaticky vykreslí nativní ovládací prvky uživatelského rozhraní pro platformy iOS, Android a Windows. Doporučujeme tento přístup, protože možnost PCL nejlépe podporuje jenom rozhraní .NET API podporovaná napříč všemi cílovými platformami a protože Xamarin. Forms umožňuje sdílet kód uživatelského rozhraní napříč platformami.

 ![Ukázka aplikace počasí v Androidu, iOS a Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

 Provedete to tak, že tyto věci sestavíte:

- [Nastavení řešení](#solution)

- [Zápis kódu sdílené datové služby](#dataservice)

- [Začněte psát sdílený kód uživatelského rozhraní](#uicode)

- [Testování aplikace pomocí emulátoru sady Visual Studio pro Android](#test)

- [Dokončete uživatelské rozhraní s nativním pohledem a chováním napříč platformami.](#finish)

> [!TIP]
> Úplný zdrojový kód pro tento projekt najdete v [úložišti Xamarin-Forms-Samples na GitHubu](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

## <a name="set-up-your-solution"></a><a name="solution"></a> Nastavení řešení
 Tyto kroky vytvoří řešení Xamarin. Forms, které obsahuje PCL pro sdílený kód a dva přidané balíčky NuGet.

1. V aplikaci Visual Studio vytvořte novou **prázdnou aplikaci (Xamarin. Forms Portable)** řešení a pojmenujte ji **WeatherApp**. Tuto šablonu můžete snadno najít tak, že do vyhledávacího pole zadáte **Xamarin. Forms** .

     Pokud tam není, možná budete muset nainstalovat Xamarin nebo povolit funkci sady Visual Studio 2015, přečtěte si téma [instalace a instalace](../cross-platform/setup-and-install.md).

     ![Vytvoření nové prázdné aplikace &#40;projektu s přenosnou&#41; Xamarin. Forms](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2. Až kliknete na OK, budete mít k dispozici několik jednotlivých projektů:

    - **WeatherApp (Portable)**: PCL, kde budete psát kód, který je sdílen napříč platformami, včetně běžné obchodní logiky a kódu uživatelského rozhraní pomocí Xamarin. Forms.

    - **WeatherApp. Droid**: projekt, který obsahuje nativní kód pro Android. Tato hodnota je nastavena jako výchozí spouštěný projekt.

    - **WeatherApp. iOS**: projekt, který obsahuje nativní kód iOS.

    - **WeatherApp. UWP**: projekt, který obsahuje kód Windows 10 UWP.

    - **WeatherApp. Windows (Windows 8.1)**: projekt, který obsahuje nativní kód Windows 8.1.

    - **WeatherApp. Winphone (Windows Phone 8,1)**: projekt obsahující nativní kód Windows Phone.

    > [!NOTE]
    > Nebudete moct odstranit žádné projekty pro platformu, na kterou necílíte. Pro účely tohoto návodu budeme odkazovat na projekty pro Android, iOS a Windows Phone 8,1. Práce s projekty UWP a Windows 8.1 je velmi podobná práci s projektem Windows Phone 8,1.

     V rámci každého nativního projektu máte přístup k nativnímu návrháři pro odpovídající platformu a v případě potřeby můžete implementovat obrazovky a funkce specifické pro platformu.

3. Upgradujte balíček NuGet Xamarin. Forms v řešení na nejnovější stabilní verzi následujícím způsobem. Tuto akci doporučujeme provést vždy, když vytvoříte nové řešení Xamarin:

    - Vyberte **nástroje > správce balíčků nuget > spravovat balíčky NuGet pro řešení**.

    - Na kartě **aktualizace** ověřte aktualizace **Xamarin. Forms** a zaškrtněte, pokud chcete aktualizovat všechny projekty v řešení. (Poznámka: nechejte všechny aktualizace pro Xamarin. Android. support nezaškrtnuto.)

    - Aktualizujte pole **verze** na **nejnovější stabilní** verzi, která je k dispozici.

    - Klikněte na **Aktualizovat**.

         ![Aktualizace balíčku NuGet pro Xamarin. Forms](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")

4. Přidejte do projektu PCL balíček **Newtonsoft.Js** a NuGet, který budete používat ke zpracování informací získaných z datové služby počasí:

    - Ve Správci balíčků NuGet (stále otevřený z kroku 3) vyberte kartu **Procházet** a vyhledejte **Newtonsoft**.

    - Vyberte **Newtonsoft.Js**.

    - Podívejte se na projekt **WeatherApp** (Jedná se o jediný projekt, ve kterém potřebujete balíček nainstalovat).

    - Zajistěte, aby se v poli **verze** nastavila **nejnovější stabilní** verze.

    - Klikněte na **Install** (Nainstalovat).

    - ![Vyhledání a instalace Newtonsoft.Jsdo balíčku NuGet](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")

5. Opakujte krok 4 pro vyhledání a instalaci balíčku **Microsoft.NET. http** .

6. Sestavte řešení a ověřte, zda nedochází k chybám sestavení.

## <a name="write-shared-data-service-code"></a><a name="dataservice"></a> Zápis kódu sdílené datové služby
 Projekt **WeatherApp (Portable)** je místo, kde budete psát kód pro přenosnou knihovnu tříd (PCL), která je sdílena napříč všemi platformami. V balíčcích aplikací pro iOS, Android a Windows Phone se automaticky zahrne do sestavení balíčky aplikací.

 Pokud chcete tuto ukázku spustit, musíte si nejdřív zaregistrovat bezplatný klíč rozhraní API na adrese [http://openweathermap.org/appid](https://openweathermap.org/appid) .

 Následující postup přidá kód do PCL pro přístup k datům z této služby počasí a jejich uložení:

1. Klikněte pravým tlačítkem na projekt **WeatherApp** a vyberte **Přidat > třídy...** V dialogovém okně **Přidat novou položku zadejte** název souboru **Weather.cs**. Tuto třídu použijete k ukládání dat z datové služby počasí.

2. Celý obsah **Weather.cs** nahraďte následujícím:

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

3. Přidejte další třídu do projektu PCL s názvem **DataService.cs** , ve kterém budete používat ke zpracování dat JSON z datové služby počasí.

4. Celý obsah **DataService.cs** nahraďte následujícím kódem:

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

5. Přidejte třetí třídu do PCL s názvem **Core** , kde vložíte sdílenou obchodní logiku, jako je například logika, která vytvoří řetězec dotazu s PSČ, zavolá datovou službu počasí a naplní instanci třídy **počasí** .

6. Nahraďte obsah **Core.cs** následujícím způsobem:

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

7. Sestavte projekt PCL **WeatherApp** , abyste se ujistili, že kód je správný.

## <a name="begin-writing-shared-ui-code"></a><a name="uicode"></a> Začněte psát sdílený kód uživatelského rozhraní
 Xamarin. Forms umožňuje implementovat sdílený kód uživatelského rozhraní v jazyce PCL. V těchto krocích přidáte obrazovku do PCL s tlačítkem, které aktualizuje svůj text daty vrácenými kódem povětrnostní datové služby přidaným v předchozí části:

1. Přidejte **stránku XAML formuláře** s názvem **WeatherPage.cs** kliknutím pravým tlačítkem myši na projekt **WeatherApp** a výběrem možnosti **Přidat > novou položku...**. V dialogovém okně **Přidat novou položku** vyhledejte text "formuláře", vyberte **stránku XAML**a pojmenujte ji **WeatherPage.cs**.

     Xamarin. Forms je založen na jazyce XAML, takže tento krok vytvoří soubor **WeatherPage. XAML** spolu s vnořeným souborem kódu na pozadí **WeatherPage.XAML.cs**. To vám umožňuje vygenerovat uživatelské rozhraní prostřednictvím XAML nebo kódu. V tomto návodu provedete některé z obou.

     ![Přidání nové stránky XAML v Xamarin. Forms](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")

2. Chcete-li přidat tlačítko na obrazovku WeatherPage, nahraďte obsah souboru WeatherPage. XAML následujícím způsobem:

    ```xaml
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
           x:Class="WeatherApp.WeatherPage">
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>
    </ContentPage>
    ```

     Všimněte si, že název tlačítka musí být definován pomocí atributu **x:Name** , takže můžete odkazovat na toto tlačítko podle názvu v rámci souboru kódu na pozadí.

3. Chcete-li přidat obslužnou rutinu události pro událost **kliknutí** na tlačítko pro aktualizaci textu tlačítka, nahraďte obsah **WeatherPage.XAML.cs** kódem níže. (Můžete změnit "60601" na jiné PSČ.)

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

4. Pokud chcete při spuštění aplikace otevřít **WeatherPage** jako první obrazovku, nahraďte výchozí konstruktor v **App.cs** následujícím kódem:

    ```csharp
    public App()
    {
        MainPage = new NavigationPage(new WeatherPage());
    }
    ```

5. Sestavte projekt PCL WeatherApp, abyste se ujistili, že kód je správný.

## <a name="test-your-app-using-the-visual-studio-emulator-for-android"></a><a name="test"></a> Testování aplikace pomocí emulátoru sady Visual Studio pro Android
 Teď jste připraveni aplikaci spustit. Pojďme teď spustit jenom Android verze, abyste ověřili, že aplikace získává data ze služby počasí. Později také spustíte verze iOS a Windows Phone po přidání dalších prvků uživatelského rozhraní. (Poznámka: Pokud používáte aplikaci Visual Studio v systému Windows 7, budete postupovat podle stejných kroků, ale místo toho se spustí Xamarin Player.)

1. Nastavte projekt **WeatherApp. Droid** jako spouštěný projekt tak, že na něj kliknete pravým tlačítkem myši a vyberete **nastavit jako spouštěný projekt**.

2. Na panelu nástrojů sady Visual Studio uvidíte **WeatherApp. Droid** , který je uveden jako cílový projekt. Vyberte jeden z emulátorů Androidu pro ladění a stiskněte klávesu **F5**. Doporučujeme použít jednu z možností **emulátoru vs** , která spustí aplikaci v emulátoru sady Visual Studio pro Android.

     ![Výběr cíle ladění emulátoru VS](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")

3. Když se aplikace spustí v emulátoru, klikněte na tlačítko **získat počasí** . Měli byste vidět, že se text tlačítka aktualizoval na **Chicago, Il**, což je vlastnost *title* dat načtených ze služby počasí.

     ![Aplikace s počasí před a po klepnutí na tlačítko](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")

## <a name="finish-the-ui-with-a-native-look-and-feel-across-platforms"></a><a name="finish"></a> Dokončete uživatelské rozhraní s nativním pohledem a chováním napříč platformami.
 Xamarin. Forms vykresluje nativní ovládací prvky uživatelského rozhraní pro každou platformu, takže vaše aplikace automaticky má nativní vzhled a chování. Chcete-li tuto skutečnost zobrazit jasně, dokončete uživatelské rozhraní se vstupním polem pro PSČ a potom zobrazte data o počasí vracená ze služby.

1. Obsah souboru **WeatherPage. XAML** nahraďte následujícím kódem. Všimněte si, že každý element je pojmenován pomocí atributu **x:Name** , jak je popsáno výše, aby element mohl být odkazován z kódu. Xamarin. Forms také poskytuje řadu [možností rozložení](/xamarin/xamarin-forms/user-interface/controls/layouts) (Xamarin.com); v tomto případě WeatherPage používá [StackLayout](/dotnet/api/Xamarin.Forms.StackLayout?view=xamarin-forms) (Xamarin.com).

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

    Všimněte si použití značky the **Platform** v Xamarin. Forms. Na **platformě** se vybere hodnota vlastnosti, která je specifická pro aktuální platformu, na které běží aplikace (viz [externí syntaxe jazyka XAML](/xamarin/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax) (Xamarin.com). Používáme ji tady k nastavení jiné barvy textu pro datová pole: bílá v Androidu a Windows Phone černou v iOS. V případě jakýchkoli vlastností a libovolných datových typů můžete provádět úpravy **specifické pro konkrétní** platformu kdekoli v jazyce XAML. V souboru kódu na pozadí můžete použít [rozhraní API zařízení. s platformou](/xamarin/xamarin-forms/platform/device) pro stejný účel.

2. V **WeatherPage.XAML.cs**Nahraďte obslužnou rutinu události **GetWeatherBtn_Clicked** kódem níže. Tento kód ověřuje, že v poli pro zadání je PSČ, načítá data pro toto PSČ, nastavuje kontext vazby celé obrazovky na výslednou instanci počasí a pak nastaví text tlačítka na "vyhledat znovu". Všimněte si, že každý popisek v uživatelském rozhraní se váže k vlastnosti třídy počasí, takže když nastavíte kontext vazby obrazovky na instanci **počasí** , tyto popisky se automaticky aktualizují.

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

3. Spusťte aplikaci na všech třech platformách – Android, iOS a Windows Phone – kliknutím pravým tlačítkem myši na příslušný projekt, výběrem možnosti nastavit jako spouštěný projekt a spuštěním aplikace buď na zařízení, nebo v emulátoru nebo simulátoru. Zadejte platné USA PSČ (například 60601) a stisknutím tlačítka získat počasí zobrazte data o počasí v této oblasti, jak je znázorněno níže. Budete samozřejmě potřebovat, aby se Visual Studio připojilo k počítači Mac OS X v síti pro projekt iOS.

    ![Ukázka aplikace počasí v Androidu, iOS a Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")

   Úplný zdrojový kód pro tento projekt je v [úložišti Xamarin-Forms-Samples na GitHubu](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).
