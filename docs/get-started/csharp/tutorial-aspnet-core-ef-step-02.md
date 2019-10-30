---
title: 'Krok 2: Vytvoření první ASP.NET Core webové aplikace'
description: Pomocí tohoto výukového kurzu a podrobného postupu vytvořte svou první webovou aplikaci ASP.NET Core.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 21959c4a0cc2b961eca43ab9724369c7aea8444b
ms.sourcegitcommit: ab18c9d850192fc9ccec10961f1126e8b0cba8da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73061139"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Krok 2: Vytvoření první ASP.NET Core webové aplikace

Pomocí tohoto výukového kurzu a podrobného postupu vytvořte svou první webovou aplikaci ASP.NET Core.

_Podívejte se na toto video a sledujte společně a vytvořte svou první aplikaci ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Spusťte Visual Studio 2019 a vytvořte nový projekt.

Spusťte Visual Studio 2019 a klikněte na **vytvořit nový projekt**. Vyberte **ASP.NET Core webové aplikace**. Vyberte šablonu **webové aplikace** a ponechejte výchozí název projektu a umístění. V rozevíracím seznamu s verzí ASP.NET Core vyberte **ASP.NET Core 2,1** nebo **ASP.NET Core 2,2**. Klikněte na **vytvořit**. Podrobnější pokyny najdete [v předchozím videu v této sérii kurzů](tutorial-aspnet-core-ef-step-01.md).

![Visual Studio 2019 volba možností projektu ASP.NET Core](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> Ujistěte se, že jste vybrali ASP .NET Core 2,1 nebo ASP.NET Core 2,2. Tento kurz není kompatibilní s ASP.NET Core 3. x.

## <a name="explore-the-new-project"></a>Prozkoumat nový projekt

V okně Průzkumník řešení na pravé straně můžete zobrazit obsah nového projektu. Jsou popsány zde.

![Visual Studio 2019 ASP.NET Core projekt](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

Složka *wwwroot* obsahuje statické soubory, které budou veřejně přístupné z webové aplikace. Obvykle obsahuje šablony stylů, soubory skriptů na straně klienta a obrázky.

### <a name="pages"></a>Stránky

Složka *Pages* obsahuje Razor Pages webu. Výchozí šablona poskytuje několik stránek, včetně stránky *index. cshtml* , která je domovskou stránkou aplikace, a také o kontaktu, kontaktu atd.

### <a name="appsettingsjson"></a>appSettings. JSON

Tento soubor obsahuje nastavení konfigurace pro lokalitu ve formátu JSON.

### <a name="programcs"></a>Program.cs

Tento soubor slouží jako vstupní bod pro aplikaci. Při spuštění aplikace se jedná o první metodu, která je spuštěna, a zodpovídá za vytvoření webového hostitele, který bude obsahovat aplikaci.

### <a name="startupcs"></a>Startup.cs

Webový hostitel vytvořený v *program.cs* odkazuje na spouštěcí třídu a volá její metody pro konfiguraci aplikace. Metoda ConfigureServices zodpovídá za nastavení všech služeb, které bude aplikace používat. Metoda `Configure` nastaví kanál požadavku HTTP aplikace. Každý požadavek prochází tímto kanálem a pracuje s jednotlivými *middlewari* .

### <a name="indexcshtml"></a>Index. cshtml

Domovská stránka webu obsahuje několik značek HTML a některé kód Razor na straně serveru. Pomocí Razor určí model stránky `IndexModel`, který se nachází v přidruženém souboru *index.cshtml.cs* . Také nastaví název stránky nastavením hodnoty v ViewData. Tato hodnota ViewData je čtena\_v souboru *layout. cshtml* , který je umístěn ve sdílené složce ve složce stránky. Soubor rozložení je sdílen mnoha Razor Pages a poskytuje běžný vzhled a chování aplikace. Obsah každé stránky se vykreslí v HTML souboru rozložení.

## <a name="run-the-application"></a>Spuštění aplikace

Nyní spusťte aplikaci a zobrazte ji v prohlížeči. Aplikaci můžete spustit pomocí **kombinace kláves Ctrl**+**F5** nebo výběrem možnosti **ladit** > **Spustit bez ladění** v nabídce sady Visual Studio.

## <a name="customize-the-application"></a>Přizpůsobení aplikace

Přidejte do souboru *index.cshtml.cs* vlastnost a nastavte její hodnotu na aktuální čas v obslužné rutině `OnGet`:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Nahraďte `<div>` obsah v *indexu. cshtml* pomocí tohoto kódu:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Spusťte aplikaci znovu. Měla by se zobrazit, že stránka nyní zobrazuje aktuální čas, ale je vždy půlnocí! To není správné.

![Projekt sady Visual Studio 2019 ASP.NET Core v prohlížeči](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Ladění aplikace

Přidejte zarážku do metody `OnGet`, kde přiřadíme hodnotu `Time` a tento čas spustí ladění aplikace.

Spuštění na řádku se zastaví a uvidíte, že `DateTime.Today` obsahuje datum, ale čas je vždycky půlnoc, protože nezahrnuje data času. 

![Projekt sady Visual Studio 2019 ASP.NET Core v prohlížeči](media/vs-2019/vs2019-breakpoint.png)

Změňte ji na použití `DateTime.Now` a pokračování v provádění. Nový kód pro `OnGet` by měl být:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

V prohlížeči by se teď měl zobrazit skutečný čas serveru, když přejdete do aplikace.

> [!NOTE]
> Výstup se může od obrázku lišit, protože výstupní formát ToShortDateTimeString závisí na aktuálním nastavení jazykové verze. Viz <xref:System.DateTime.ToShortTimeString>.

![Projekt sady Visual Studio 2019 ASP.NET Core v prohlížeči](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Další kroky

V dalším videu se dozvíte, jak přidat podporu dat do aplikace.

[Kurz: práce s daty v aplikaci ASP.NET Core](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Viz také:

- [Kurz: Vytvoření webové aplikace v Razor Pages s využitím ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
