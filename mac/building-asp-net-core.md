---
title: Vytváření ASP.NET základních aplikací
description: Tento článek popisuje, jak začít s ASP.NET v Sadě Visual Studio pro Mac, včetně instalace a vytvoření nového projektu.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: 5600fd2f0b6d83a3bd27350a4d4f0137ea44ced2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75398287"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Vytváření aplikací ASP.NET Core v sadě Visual Studio pro Mac

ASP.NET Core je open source a multiplatformní framework pro vytváření moderních cloudových internetových aplikací, jako jsou webové aplikace a služby, aplikace IoT a mobilní back-endy. ASP.NET základní aplikace lze spustit na [.NET Core](https://www.microsoft.com/net/core/platform) nebo na .NET Framework runtimes. Byl navržen tak, aby poskytoval optimalizovaný rámec pro vývoj aplikací, které se nasazují do cloudu nebo běží místně. Skládá se z modulárních komponent s minimální režií, takže si zachováte flexibilitu při konstrukci řešení. Aplikace ASP.NET Core můžete vyvíjet a spouštět na příčce na Windows, Macu a Linuxu. ASP.NET Core je open source na [GitHubu](https://github.com/aspnet/home).

V tomto testovacím prostředí vytvoříte a prozkoumáte aplikaci ASP.NET Core pomocí Visual Studia for Mac.

## <a name="objectives"></a>Cíle

> [!div class="checklist"]
> * Vytvoření webové aplikace ASP.NET Core
> * Prozkoumejte ASP.NET hosting, konfiguraci a middlewarový model
> * Ladění webové aplikace ASP.NET Core

## <a name="prerequisites"></a>Požadavky

- [Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Zamýšlená cílová skupina

Tato testovací prostředí je určena pro vývojáře, kteří jsou obeznámeni s C#, i když hluboké zkušenosti není vyžadováno.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Úkol 1: Vytvoření nové aplikace ASP.NET Core

1. Spusťte **Visual Studio pro Mac**.

2. Vyberte **možnost Soubor > nové řešení**.

3. Vyberte kategorii **.NET Core > App** a šablonu **ASP.NET Core Web App (C#).** Klikněte na **Další**.

    ![](media/netcore-image1.png)

4. Zadejte název **"CoreLab"** a kliknutím na **Vytvořit** vytvořte projekt. Bude chvíli trvat, než to dokončíme.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Úkol 2: Prohlídka řešení

1. Výchozí šablona vytvoří řešení s jedním ASP.NET core projekt s názvem **CoreLab**. Rozbalte uzel projektu vystavit jeho obsah.

    ![](media/netcore-image3.png)

2. Tento projekt následuje model-view-controller (MVC) paradigma poskytnout jasné rozdělení odpovědnosti mezi data (modely), prezentace (zobrazení) a funkce (řadiče). Otevřete soubor **HomeController.cs** ze složky **Řadiče.**

    ![](media/netcore-image4.png)

3. **HomeController** class-by convention zpracovává všechny příchozí požadavky, které začínají **/Home**. Metoda **Index** zpracovává požadavky na kořen adresáře `http://site.com/Home`(například) a další metody zpracovávají požadavky na jejich pojmenované cesty `http://site.com/Home/About`na základě konvence, jako je například **About()** zpracování požadavků na . Samozřejmě, to vše je konfigurovatelné. Jeden pozoruhodný je, že **HomeController** je výchozí řadič v novém projektu, takže`http://site.com`požadavky na kořen webu ( ) by projít `http://site.com/Home` `http://site.com/Home/Index` **Index()** **HomeController** stejně jako požadavky na nebo .

    ![](media/netcore-image5.png)

4. Projekt má také **zobrazení** složky, která obsahuje další složky, které mapovat na každý řadič (stejně jako jeden pro **sdílená** zobrazení. Například soubor CSHTML zobrazení (rozšíření HTML) pro **/Home/About** path by byl na **adrese Zobrazení/Domů/About.cshtml**. Otevřete ten soubor.

    ![](media/netcore-image6.png)

5. Tento soubor CSHTML používá syntaxi Razor k vykreslení HTML na základě kombinace standardních tagů a vložených C#. Další informace naleznete v [online dokumentaci](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![](media/netcore-image7.png)

6. Řešení také obsahuje **složku wwwroot,** která bude kořenem vašeho webu. Statický obsah webu, například CSS, obrázky a knihovny JavaScriptu, můžete umístit přímo na cesty, na kterých byste chtěli, aby byly při nasazení webu.

    ![](media/netcore-image8.png)

7. Existují také různé konfigurační soubory, které slouží ke správě projektu, jeho balíčky a aplikace za běhu. Například výchozí [konfigurace](/aspnet/core/fundamentals/configuration) aplikace je uložena v **souboru appsettings.json**. Pod souborem appsettings.json je vnořeno **nastavení aplikace. Soubor Development.json.** Zde můžete přepsat některé nebo všechna tato nastavení na základě prostředí. Visual Studio for Mac bude vnořit soubory tímto způsobem pomocí stejné logiky jako Visual Studio pro Windows, takže soubory, které potřebujete k přístupu častěji jsou v popředí. 

    ![](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Úkol 3: Pochopení způsobu hostování aplikace

1. Z **Průzkumníka řešení**otevřete **Program.cs**. Toto je zaváděcí nástroj, který spustí vaši aplikaci.

    ![](media/netcore-image10.png)

2. I když jsou tu jen dva řádky kódu, jsou podstatné. Pojďme je rozebrat. Nejprve je vytvořen nový **WebHostBuilder.** ASP.NET Základní aplikace vyžadují hostitele, ve kterém se má spustit. Hostitel musí implementovat rozhraní **IWebHost,** které zveřejňuje kolekce funkcí a služeb a metodu **Start.** Hostitel je obvykle vytvořen pomocí instance **WebHostBuilder**, který vytváří a vrací instanci **WebHost.** **WebHost** odkazuje na server, který bude zpracovávat požadavky.

    ![](media/netcore-image11.png)

3. Zatímco **WebHostBuilder** je zodpovědný za vytvoření hostitele, který bude bootstrap server pro aplikaci, vyžaduje, abyste poskytli server, který implementuje **IServer**. Ve výchozím nastavení se jedná **[o Kestrel](/aspnet/core/fundamentals/servers/kestrel)**, webový server pro různé platformy pro ASP.NET Core založený na **libuvu**, což je asynchronní knihovna vstupně-v.o.

    ![](media/netcore-image12.png)

4. Dále je nastaven kořen obsahu serveru. Určuje, kde vyhledává soubory obsahu, například soubory Zobrazení MVC. Výchozí kořenový obsah je složka, ze které je aplikace spuštěna.

    ![](media/netcore-image13.png)

5. Pokud aplikace musí pracovat s webovým serverem Internetové informační služby (IIS), metoda **UseIISIntegration** by měla být volána jako součást vytváření hostitele. Že to nekonfiguruje server, stejně jako **UseKestrel** dělá. Chcete-li používat iš is s jádrem ASP.NET, musíte zadat **useKestrel** i **UseIISIntegration**. **Kestrel** je navržen tak, aby byl spuštěn za proxy serverem a neměl by být nasazen přímo směrem k internetu. **Aplikace UseIISIntegration** určuje službu IIS jako server reverzního proxy serveru, ale je relevantní pouze při spuštění v počítačích se službou IIS. Pokud aplikaci nasadíte do Windows, nechte ji v něm. Jinak to nebolí.

    ![](media/netcore-image14.png)

6. Je to čistší praxe oddělit zatížení nastavení od aplikace bootstrapping. Chcete-li snadno provést, **UseStartup** je volána určit, že **spuštění** třídy má být volána pro načítání nastavení a další úlohy při spuštění, jako je například vkládání middleware do kanálu HTTP. Můžete mít více **UseStartup** volání s očekáváním, že každý z nich přepíše předchozí nastavení podle potřeby.

    ![](media/netcore-image15.png)

7. Posledním krokem při vytváření **IWebHost** je volání **Build**.

    ![](media/netcore-image16.png)

8. Zatímco **třídy IWebHost** jsou nutné k implementaci neblokující **start**, ASP.NET základní projekty mají metodu rozšíření s názvem **Spustit,** která zalomí **Start** s blokující kód, takže nemusíte ručně zabránit ukončení metody okamžitě.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Úloha 4: Spuštění a ladění aplikace

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu **CoreLab** a vyberte **možnosti**.

    ![](media/netcore-image18.png)

2. Dialogové okno **Možnosti projektu** obsahuje vše, co potřebujete k nastavení způsobu, jakým je aplikace vytvořena a spuštěna. Z levého panelu vyberte **spustit > konfigurace > výchozím** uzlu.

3. Zaškrtněte **políčko Spustit na externí konzoli** a odškrtnout **políčko Pozastavit výstup konzoly**. Obvykle samoobslužné aplikace nebude mít jeho konzole viditelné, ale místo toho protokolu výsledků **výstupu** pad. Pro účely této laboratoře, ukážeme to v samostatném okně stejně, i když nemusíte dělat, že během normálního vývoje.

4. Klikněte na tlačítko **OK**.

    ![](media/netcore-image19.png)

5. Stisknutím **klávesy F5** vytvořte a spusťte aplikaci. Případně můžete vybrat **spustit > spustit ladění start**.

6. Visual Studio pro Mac spustí dvě okna. První je okno konzoly, které poskytuje zobrazení do samoobslužné serverové aplikace.

    ![](media/netcore-image20.png)

7. Druhý je typické okno prohlížeče pro testování webu. Pokud prohlížeč ví, tato aplikace by mohla být hostována kdekoli. Klepnutím na **tlačítko O** přejděte na tuto stránku.

    ![](media/netcore-image21.png)

8. Stránka o stránce mimo jiné vykreslí nějaký text nastavený v ovladači.

    ![](media/netcore-image22.png)

9. Nechte obě okna otevřená a vraťte se do Visual Studia pro Mac. Otevřete **controllers/HomeController.cs,** pokud ještě není otevřená.

    ![](media/netcore-image23.png)

10. Nastavte zarážku v prvním řádku metody **About.** Můžete to udělat tak, že kliknete na okraj nebo nastavíte kurzor na řádku a stisknete **klávesu F9**. Tento řádek nastaví některá data v kolekci **ViewData,** která je vykreslena na stránce CSHTML na **adrese Views/Home/About.cshtml**.

    ![](media/netcore-image24.png)

11. Vraťte se do prohlížeče a aktualizujte stránku o. Tím se aktivuje zarážka ve Visual Studiu pro Mac.

12. Najeďte myší na člen **ViewData** a zobrazte jeho data. Můžete také rozbalit jeho podřízené členy, abyste viděli vnořená data.

    ![](media/netcore-image25.png)

13. Odeberte zarážku aplikace stejnou metodou, kterou jste použili k jeho přidání.

14. Otevřít **zobrazení/Domů/About.cshtml**.

15. Změňte text **"další"** na **"změněno"** a uložte soubor.

    ![](media/netcore-image26.png)

16. Pokračujte v provádění stisknutím tlačítka **Pokračovat.**

    ![](media/netcore-image27.png)

17. Chcete-li zobrazit aktualizovaný text, vraťte se do okna prohlížeče. Tato změna může být provedena kdykoli a nemusí nutně vyžadovat zarážku ladicího programu. Pokud se změna neprojeví okamžitě, aktualizujte prohlížeč.

    ![](media/netcore-image28.png)

18. Zavřete okno testovacího prohlížeče a konzolu aplikace. Tím se zastaví ladění také.

## <a name="task-5-application-startup-configuration"></a>Úloha 5: Konfigurace spuštění aplikace

1. V **Průzkumníku řešení**otevřete **Startup.cs**. Můžete si všimnout, některé červené vlnovky zpočátku jako NuGet balíčky jsou obnovovány na pozadí a kompilátor Roslyn vytváří úplný obraz závislostí projektu.

    ![](media/netcore-image29.png)

2. Vyhledejte metodu **Po spuštění.** Tato část definuje počáteční konfiguraci aplikace a je hustě zabalena. Pojďme to rozebrat.

    ![](media/netcore-image30.png)

3. Metoda začíná inicializací **ConfigurationBuilder** a nastavením jeho základní cesty.

    ![](media/netcore-image31.png)

4. Dále načte požadovaný soubor **appsettings.json.**

    ![](media/netcore-image32.png)

5. Poté se pokusí načíst soubor **appsettings.json** specifické pro prostředí, který by přepsat existující nastavení. Například se jedná o poskytované **nastavení aplikace. Soubor Development.json** používaný pro dané konkrétní prostředí. Chcete-li se podívat na další informace o konfiguraci v ASP.NET Core, podívejte se [na dokumenty](/aspnet/core/fundamentals/configuration).

    ![](media/netcore-image34.png)

6. Nakonec proměnné prostředí jsou přidány do tvůrce konfigurace a konfigurace je sestavena a nastavena pro použití.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Úkol 6: Vkládání middlewaru aplikace

1. Vyhledejte metodu **Configure** ve třídě **Startup.** Toto je místo, kde je nakonfigurován veškerý middleware tak, aby mohl být vložen do kanálu HTTP a použit ke zpracování každého požadavku na server. Zatímco tato metoda je volána pouze jednou, obsah metody (například **UseStaticFiles**) může být proveden na každém požadavku.

    ![](media/netcore-image36.png)

2. Můžete také přidat další middleware, které mají být provedeny jako součást kanálu. Přidejte kód níže po **aplikaci. Použití StaticFiles** automaticky přidat **x-test** záhlaví každé odchozí odpovědi. Technologie IntelliSense vám pomůže dokončit kód při psaní.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Stisknutím **klávesy F5** sestavíte a spusťte projekt.

4. Můžeme použít prohlížeč ke kontrole záhlaví ověřit, že jsou přidány. Níže uvedené pokyny jsou pro Safari, ale můžete udělat totéž v [Prohlížeči Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) nebo [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Jakmile prohlížeč načte web, vyberte **předvolby safari >**.

6. Na kartě **Upřesnit** zaškrtněte **v řádku nabídek Zobrazit vývoj** a zavřete dialogové okno.

    ![](media/netcore-image37.png)

7. Vyberte **možnost Rozvíjet > Zobrazit zdroje stránky**.

8. Aktualizujte okno prohlížeče tak, aby nově otevřené vývojářské nástroje mohly sledovat a analyzovat provoz a obsah.

9. Ve výchozím nastavení bude stránka HTML localhost vykreslená serverem.

    ![](media/netcore-image38.png)

10. Rozbalte **postranní panel Podrobnosti**.

    ![](media/netcore-image39.png)

11. Přejděte na konec postranního panelu a zobrazí temeno odpovědi přidané v kódu dříve.

    ![](media/netcore-image40.png)

12. Pokud je okno prohlížeče a konzola splněna, zavřete ji.

## <a name="summary"></a>Souhrn

V této laboratoři jste se naučili, jak začít vyvíjet aplikace ASP.NET Core pomocí Visual Studia pro Mac. Pokud chcete prozkoumat vývoj úplnější aplikace pro databázi filmů, přečtěte si informace [o tématu Začínáme s ASP.NET základní mvc](/aspnet/core/tutorials/first-mvc-app/start-mvc) kurz.
