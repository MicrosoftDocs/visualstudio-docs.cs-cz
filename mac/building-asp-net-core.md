---
title: Sestavování ASP.NET Corech aplikací
description: Tento článek popisuje, jak začít s ASP.NET v Visual Studio pro Mac, včetně instalace a vytvoření nového projektu.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.topic: how-to
ms.openlocfilehash: 47ddfa11b4c05896037c1fb18e285d46fc79520b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88214611"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Vytváření aplikací ASP.NET Core v sadě Visual Studio pro Mac

ASP.NET Core je open source architektura pro různé platformy pro vytváření moderních cloudových aplikací připojených k Internetu, jako jsou webové aplikace a služby, aplikace IoT a mobilní back-endy. Aplikace ASP.NET Core mohou běžet v prostředí [.NET Core](https://www.microsoft.com/net/core/platform) nebo v .NET Framework modulech runtime. Byla navržena tak, aby poskytovala optimalizované vývojové rozhraní pro aplikace, které jsou nasazeny do cloudu nebo místně spuštěné. Skládá se z modulárních komponent s minimálními nároky, takže při vytváření vašich řešení si zachováte flexibilitu. Můžete vyvíjet a spouštět aplikace ASP.NET Core pro různé platformy v systémech Windows, Mac a Linux. ASP.NET Core je open source na [GitHubu](https://github.com/aspnet/home).

V tomto testovacím prostředí vytvoříte a prozkoumáte ASP.NET Core aplikaci pomocí Visual Studio pro Mac.

## <a name="objectives"></a>Cíle

> [!div class="checklist"]
> * Vytvoření webové aplikace ASP.NET Core
> * Prozkoumejte ASP.NET Core hostování, konfigurace a middlewarového modelu
> * Ladění ASP.NET Core webové aplikace

## <a name="prerequisites"></a>Předpoklady

- [Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Zamýšlená cílová skupina

Toto testovací prostředí je určené pro vývojáře, kteří znají jazyk C#, ale hloubkové prostředí není nutné.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Úloha 1: vytvoření nové aplikace ASP.NET Core

1. Spusťte **Visual Studio pro Mac**.

2. Vyberte **soubor > nové řešení**.

3. Vyberte kategorii **aplikace > .NET Core** a šablonu **ASP.NET Core webové aplikace (C#)** . Klikněte na **Next** (Další).

    ![Snímek obrazovky ukazující, jak vybrat šablonu webové aplikace pro nový projekt.](media/netcore-image1.png)

4. Zadejte název **"CoreLab"** a kliknutím na **vytvořit** vytvořte projekt. Dokončení této akce bude chvíli trvat.

    ![Snímek obrazovky s konfigurací webové aplikace a přidáním názvu projektu.](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Úkol 2: Seznámení s řešením

1. Výchozí šablona vytvoří řešení s jedním ASP.NET Core projektem s názvem **CoreLab**. Rozbalením uzlu projektu vystavte jeho obsah.

    ![Snímek obrazovky uzlu projektu řešení, aby se zobrazil jeho obsah, včetně složek a souborů](media/netcore-image3.png)

2. Tento projekt následuje po paradigmatu Model-View-Controller (MVC) a poskytuje jasné rozdělení zodpovědnosti mezi daty (modely), prezentací (zobrazeními) a funkcemi (kontroléry). Otevřete soubor **HomeController.cs** ze složky **Controllers** .

    ![Snímek projektu řešení s třídou C# s názvem HomeController vybrán.](media/netcore-image4.png)

3. Konvence třídy **HomeController** – zpracovává všechny příchozí požadavky, které začínají na **/Home**. Metoda **index** zpracovává požadavky do kořenové složky adresáře (jako `http://site.com/Home` ) a další metody zpracovávají požadavky na jejich pojmenovanou cestu na základě konvence, jako je například zpracování žádostí **o ()** `http://site.com/Home/About` . To je samozřejmě vše konfigurovatelné. Jednou z důležitých verzí je, že **HomeController** je výchozí kontroler v novém projektu, takže požadavky na kořen webu ( `http://site.com` ) by procházejí prostřednictvím **indexu ()** **HomeController** , stejně jako žádosti `http://site.com/Home` nebo `http://site.com/Home/Index` .

    ![Snímek obrazovky třídy jazyka C# s názvem HomeController.](media/netcore-image5.png)

4. Projekt má také složku **zobrazení** , která obsahuje další složky, které jsou namapovány na jednotlivé řadiče (a také na jeden pro **sdílená** zobrazení. Například soubor zobrazení CSHTML (rozšíření HTML) pro cestu **/Home/about** by měl být v **zobrazení/domů/o. cshtml**. Otevřete tento soubor.

    ![Snímek projektu řešení se souborem C S H T M L s názvem o vybrané.](media/netcore-image6.png)

5. Tento soubor CSHTML používá syntaxe Razor k vykreslování kódu HTML na základě kombinace standardních značek a vloženého jazyka C#. Další informace najdete v [online dokumentaci](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![Snímek obrazovky části souboru C S H T M L zobrazující syntaxe Razor.](media/netcore-image7.png)

6. Řešení obsahuje také složku **wwwroot** , která bude kořenem vašeho webu. Statický obsah webu, jako jsou CSS, obrázky a knihovny JavaScriptu, můžete umístit přímo na cesty, ve kterých byste měli při nasazení webu.

    ![Snímek obrazovky s vybraným kořenovou složkou w w w](media/netcore-image8.png)

7. K dispozici jsou také různé konfigurační soubory, které slouží ke správě projektu, jeho balíčků a aplikace za běhu. Například výchozí [Konfigurace](/aspnet/core/fundamentals/configuration) aplikace je uložena v **appsettings.js**. Vnořený pod appsettings.jsv souboru je **appsettings.Development.jsv** souboru. Tady můžete potlačit některá nebo všechna tato nastavení v jednotlivých prostředích. Visual Studio pro Mac bude tímto způsobem vnořovat soubory pomocí stejné logiky jako aplikace Visual Studio pro Windows, takže soubory, které potřebujete získat častěji, jsou v Forefrontu. 

    ![Snímek obrazovky znázorňující zobrazení podrobností se zvoleným souborem JSON](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Úloha 3: princip hostování aplikace

1. Z **Průzkumník řešení**otevřete **program.cs**. Toto je zaváděcí nástroj, který spustí vaši aplikaci.

    ![Snímek obrazovky řešení s vybraným zdrojovým souborem C# s názvem program](media/netcore-image10.png)

2. I když zde jsou pouze dva řádky kódu, jsou zásadní. Pojďme je rozdělit. Nejprve se vytvoří nový **WebHostBuilder** . ASP.NET Core aplikace vyžadují hostitele, ve kterém se má provést. Hostitel musí implementovat rozhraní **IWebHost** , které zpřístupňuje kolekce funkcí a služeb a metodu **Start** . Hostitel je obvykle vytvořen pomocí instance třídy **WebHostBuilder**, která sestaví a vrací instanci **webhost** . **Webhost** odkazuje na server, který bude zpracovávat požadavky.

    ![Snímek obrazovky s hlavní metodou jazyka C# s příkazem, který inicializuje proměnnou s názvem host s typem WebHostBuilder.](media/netcore-image11.png)

3. I když je **WebHostBuilder** zodpovědný za vytvoření hostitele, který spustí server aplikace, vyžaduje poskytnutí serveru, který implementuje **IServer**. Ve výchozím nastavení se jedná o **[Kestrel](/aspnet/core/fundamentals/servers/kestrel)** webový server pro různé platformy pro ASP.NET Core založený na **libuv**, což je asynchronní vstupně-výstupní knihovna pro různé platformy.

    ![Snímek obrazovky Main Method v jazyce C# zvýraznění proměnné hostitele nastavení serveru pomocí metody UseKestrel](media/netcore-image12.png)

4. V dalším kroku je nastaven kořen obsahu serveru. To určuje, kde hledá soubory obsahu, například soubory zobrazení MVC. Výchozí kořen obsahu je složka, ze které se aplikace spouští.

    ![Snímek obrazovky Main Method v jazyce C# zvýraznění proměnné hostitele nastavení kořenového adresáře obsahu pro server pomocí metody UseContentRoot](media/netcore-image13.png)

5. Pokud aplikace musí spolupracovat s webovým serverem Internetová informační služba (IIS), měla by být metoda **UseIISIntegration** volána jako součást sestavení hostitele. To neprovádí konfiguraci serveru, jako je **UseKestrel** . Chcete-li použít službu IIS s ASP.NET Core, je nutné zadat jak **UseKestrel** , tak **UseIISIntegration**. **Kestrel** je navržený tak, aby se spouštěl za proxy serverem a neměl by se nasazovat přímo na Internet. **UseIISIntegration** Určuje službu IIS jako reverzní proxy server, ale je relevantní pouze při spuštění na počítačích, které mají službu IIS. Pokud nasadíte aplikaci do systému Windows, ponechte ji v systému. Nesnížit jinak.

    ![Snímek obrazovky Main Method v jazyce C# zvýraznění proměnné hostitele nastavení reverzních proxy server s metodou UseIISIntegration](media/netcore-image14.png)

6. Je to čisticí postup, který odděluje načítání nastavení z zavedení aplikace. Aby to bylo možné snadno, je volána metoda **UseStartup** , která určuje, zda má být **spouštěcí** třída volána pro načítání nastavení a další úlohy po spuštění, například vložení middlewaru do kanálu http. Je možné, že máte několik volání **UseStartup** s očekáváním, že každé z nich Přepisuje předchozí nastavení podle potřeby.

    ![Snímek obrazovky Main Method v jazyce C# zvýraznění proměnné hostitele nastavení spouštěcí třídy pomocí možnosti UseStartup](media/netcore-image15.png)

7. Posledním krokem při vytváření **IWebHost** je volání **buildu**.

    ![Snímek z hlavní metody C# zvýrazňující proměnnou hostitele metodou sestavení.](media/netcore-image16.png)

8. I když třídy **IWebHost** jsou vyžadovány k implementaci neblokujícího **spuštění**, ASP.NET Core projekty mají metodu rozšíření s názvem **Run** , která zabalí **začátek** s blokujícím kódem, takže nemusíte ručně zabránit, aby byla metoda ukončena okamžitě.

    ![Snímek obrazovky s hlavní metodou jazyka C# zvýraznění příkazu pro spuštění hostitele příkazu](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Úloha 4: spuštění a ladění aplikace

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu **CoreLab** a vyberte **možnost možnosti**.

    ![Snímek obrazovky znázorňující kontextovou nabídku řešení CoreLab, zvýraznění možností.](media/netcore-image18.png)

2. Dialog **Možnosti projektu** obsahuje vše, co potřebujete k úpravě způsobu sestavení a spuštění aplikace. V levém panelu vyberte **Konfigurace spustit > > výchozí** uzel.

3. Kontrolovat **spuštění na externí konzole** a zrušit kontrolu **výstupu konzoly pozastavit**. Obvykle by se konzola aplikace v místním prostředí nezobrazovala, ale místo toho se do panelu **výstupu** zaprotokoluje jeho výsledky. Pro účely tohoto testovacího prostředí ji zobrazíme v samostatném okně, i když to nemusíte dělat během normálního vývoje.

4. Klikněte na **OK**.

    ![Snímek obrazovky s kartou pro obecné spuštění konfigurace s vybranou možnost spustit u externí konzoly a pozastavit výstup konzoly nebyl vybrán.](media/netcore-image19.png)

5. Stiskněte **F5**, aby se aplikace sestavila a spustila. Případně můžete vybrat **spustit > spustit ladění**.

6. Visual Studio pro Mac spustí dvě okna. První je okno konzoly, které nabízí zobrazení serverové aplikace s místním hostitelem.

    ![Snímek obrazovky s oknem konzoly pro serverovou aplikaci hostovanou na sebe](media/netcore-image20.png)

7. Druhým je typické okno prohlížeče k otestování lokality. Pokud prohlížeč ví, že tato aplikace může být hostována kdekoli. Kliknutím na tlačítko **o** přejděte na tuto stránku.

    ![Snímek obrazovky znázorňující okno prohlížeče pro otestování webu a zvýrazňování možnosti o](media/netcore-image21.png)

8. Kromě jiných věcí stránka o stránku vykresluje nějaký text nastavený v kontroleru.

    ![Snímek obrazovky znázorňující výsledek výběru možnosti o produktu, což je stránka o produktu](media/netcore-image22.png)

9. Nechte Windows otevřené a vraťte se k Visual Studio pro Mac. Otevřete **Controllers/HomeController. cs** , pokud ještě není otevřený.

    ![Snímek obrazovky s vybraným řešením pro třídu C# HomeController.](media/netcore-image23.png)

10. Nastavte zarážku na prvním řádku metody **About** . Můžete to udělat tak, že kliknete na okraj nebo nastavíte kurzor na řádku a stisknete **F9**. Tento řádek nastaví některá data v kolekci **ViewData** , která se vykreslí na stránce cshtml na **views/Home/About. cshtml**.

    ![Snímek obrazovky znázorňující metodu about se sadou zarážek](media/netcore-image24.png)

11. Vraťte se do prohlížeče a aktualizujte stránku o produktu. Tím se aktivuje zarážka v Visual Studio pro Mac.

12. Myš nad členem **ViewData** , aby se zobrazila jeho data. Můžete také rozbalit jeho podřízené členy, aby se zobrazila vnořená data.

    ![Snímek obrazovky znázorňující zarážku s rozbalenými daty](media/netcore-image25.png)

13. Odeberte zarážku aplikace pomocí stejné metody, jakou jste použili k jejímu přidání.

14. Otevřete **zobrazení/domů/o. cshtml**.

15. Změňte text **"Další"** na **"změněno"** a uložte soubor.

    ![Snímek obrazovky se souborem C S H T M L s názvem o se změnou jeho textu](media/netcore-image26.png)

16. Kliknutím na tlačítko **pokračovat** můžete pokračovat v provádění.

    ![Snímek obrazovky okna sady Visual Studio zvýraznění tlačítka pro pokračování](media/netcore-image27.png)

17. Pokud se chcete podívat na aktualizovaný text, vraťte se do okna prohlížeče. Tato změna se může provést kdykoli a nemusela by nutně vyžadovat zarážku ladicího programu. Aktualizujte prohlížeč, pokud se změna neprojeví okamžitě.

    ![Snímek obrazovky se stránkou o aplikaci tentokrát se změněným textem.](media/netcore-image28.png)

18. Zavřete okno testovacího prohlížeče a konzolu aplikace. Tím se zastaví i ladění.

## <a name="task-5-application-startup-configuration"></a>Úkol 5: konfigurace spuštění aplikace

1. Z **Průzkumník řešení**otevřete **Startup.cs**. Všimněte si, že některé červené vlnovky jsou zpočátku obnoveny na pozadí a kompilátor Roslyn vytváří kompletní přehled závislostí projektu.

    ![Snímek obrazovky řešení se souborem třídy jazyka C# s názvem Startup Selected.](media/netcore-image29.png)

2. Vyhledejte metodu **spuštění** . Tato část definuje počáteční konfiguraci aplikace a je zhuštěná. Pojďme si ji rozdělit na jednotlivé kroky.

    ![Snímek obrazovky znázorňující metodu spuštění třídy Startup](media/netcore-image30.png)

3. Metoda začíná inicializací **nerozšiřuje configurationbuilder** a nastavením jeho základní cesty.

    ![Snímek obrazovky metody spuštění se zobrazením příkazu, který inicializuje proměnnou s názvem Builder s typem nerozšiřuje configurationbuilder.](media/netcore-image31.png)

4. V dalším kroku načte požadovaný **appsettings.jsdo** souboru.

    ![Snímek obrazovky metody spuštění, která zobrazuje proměnnou tvůrce pomocí metody AddJsonFile k přidání souboru JSON s názvem appSettings.](media/netcore-image32.png)

5. Potom se pokusí načíst **appsettings.jspro** konkrétní prostředí, které by přepsaly stávající nastavení. Jedná se například o **appsettings.Development.jsv** souboru používaném pro toto konkrétní prostředí. Další informace o konfiguraci v ASP.NET Core najdete v [dokumentaci](/aspnet/core/fundamentals/configuration).

    ![Snímek obrazovky metody spuštění, která zobrazuje proměnnou tvůrce pomocí metody AddJsonFile k přidání souboru JSON pro konkrétní prostředí.](media/netcore-image34.png)

6. Nakonec jsou proměnné prostředí přidány do nástroje Configuration Builder a konfigurace je sestavena a nastavena pro použití.

    ![Snímek obrazovky metody spuštění, která zobrazuje proměnnou prostředí pro přidání proměnných prostředí a následné použití metody sestavení k sestavení konfigurace.](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Úloha 6: vložení middlewaru aplikace

1. Vyhledejte metodu **Configure** ve třídě **Startup** . Tady je místo, kde je nakonfigurované všechny middleware, aby je bylo možné vložit do kanálu HTTP a použít ke zpracování všech požadavků na server. I když je tato metoda volána pouze jednou, může být obsah metod (například **UseStaticFiles**) proveden při každém požadavku.

    ![Snímek obrazovky znázorňující metodu Configure ve třídě Startup](media/netcore-image36.png)

2. Můžete také přidat další middleware, který bude spuštěn jako součást kanálu. Přidejte kód níže po **aplikaci. UseStaticFiles** automaticky přidat hlavičku **X-test** do každé odchozí odpovědi. Technologie IntelliSense pomůže doplňovat kód při psaní.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Stisknutím klávesy **F5** Sestavte a spusťte projekt.

4. Pomocí prohlížeče můžeme zkontrolovat hlavičky a ověřit, zda jsou přidány. Následující pokyny jsou pro Safari, ale můžete je dělat stejně jako v [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) nebo v [prohlížeči Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Jakmile prohlížeč načte lokalitu, vyberte možnost **Safari > předvolby**.

6. Na kartě **Upřesnit** klikněte na příkaz **Zobrazit nabídku vývoje v řádku nabídek** a zavřete dialogové okno.

    ![Snímek obrazovky s podoknem Upřesnit v dialogovém okně Předvolby prohlížeče Safari s vybranou možností zobrazit nabídku vývoje v panelu nabídek](media/netcore-image37.png)

7. Vyberte možnost **vyvinout > zobrazit prostředky stránky**.

8. Aktualizujte okno prohlížeče tak, aby nově otevřené vývojářské nástroje mohly sledovat a analyzovat provoz a obsah.

9. Stránka HTML localhost vykreslená serverem bude položka vybraná jako výchozí.

    ![Snímek obrazovky se zvýrazněnou stránkou localhost H T M L.](media/netcore-image38.png)

10. Rozbalte **postranní panel podrobností**.

    ![Snímek obrazovky zvýraznění ovládacího prvku, který se má použít k rozbalení bočního panelu podrobností](media/netcore-image39.png)

11. Posuňte se k dolnímu okraji bočního panelu, abyste viděli hlavičku odpovědi přidanou v kódu dříve.

    ![Snímek obrazovky se zvýrazněnou hlavičkou odpovědi s názvem XTest s hodnotou testovací hodnoty.](media/netcore-image40.png)

12. Po splnění tohoto okna zavřete okno prohlížeče a konzolu.

## <a name="summary"></a>Shrnutí

V tomto testovacím prostředí jste se naučili, jak začít vyvíjet ASP.NET Core aplikace pomocí Visual Studio pro Mac. Pokud chcete prozkoumat vývoj více kompletních databázových aplikací filmů, přečtěte si kurz Začínáme [s ASP.NET Core MVC](/aspnet/core/tutorials/first-mvc-app/start-mvc) .
