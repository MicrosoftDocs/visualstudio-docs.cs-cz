---
title: 'Krok 2: Vytvoření první ASP.NET základní webové aplikace'
description: Vytvořte si první ASP.NET Core Web App s tímto instruktážním videu a podrobnými pokyny.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1d382e83aa9672cfdcbdca64b89be79d090f2aac
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580085"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Krok 2: Vytvoření první webové aplikace ASP.NET Core

Vytvořte si první ASP.NET Core Web App s tímto instruktážním videu a podrobnými pokyny.

_Podívejte se na toto video a postupujte podle pokynů a vytvořte si první ASP.NET aplikaci Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Spuštění Visual Studia 2019 a vytvoření nového projektu

Spusťte Visual Studio 2019 a klikněte na **Vytvořit nový projekt**. Zvolte **ASP.NET základní webovou aplikaci**. Zvolte šablonu **webové aplikace** a zachovejte výchozí název a umístění projektu. V rozevíracím období s verzí ASP.NET Core zvolte **ASP.NET Core 2.1** nebo **ASP.NET Core 2.2**. Klikněte na **Vytvořit**. Podrobnější pokyny naleznete [v předchozím videu v této sérii kurzů](tutorial-aspnet-core-ef-step-01.md).

![Visual Studio 2019 Zvolte ASP.NET základní možnosti projektu](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> Ujistěte se, že jste zvolili asp .NET Core 2.1 nebo ASP.NET Core 2.2. Tento výukový program není kompatibilní s ASP.NET Core 3.x.

## <a name="explore-the-new-project"></a>Prozkoumejte nový projekt

V okně průzkumníka řešení vpravo můžete zobrazit obsah nového projektu. Jsou popsány zde.

![Základní projekt Visual Studia 2019 ASP.NET](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

Složka *wwwroot* obsahuje statické soubory, které budou veřejně přístupné z webové aplikace. Obvykle obsahuje šablony stylů, soubory skriptů na straně klienta a obrázky.

### <a name="pages"></a>Stránky

Složka *Stránky* obsahuje stránky Razor stránek webu. Výchozí šablona obsahuje několik stránek, včetně stránky *Index.cshtml,* která je domovskou stránkou aplikace, a také O, Kontakt a tak dále.

### <a name="appsettingsjson"></a>appsettings.json

Tento soubor obsahuje nastavení konfigurace webu ve formátu JSON.

### <a name="programcs"></a>Program.cs

Tento soubor funguje jako vstupní bod aplikace. Při spuštění aplikace je jeho Hlavní metoda první metodou, která je spuštěna a je zodpovědná za vytvoření webového hostitele, který bude obsahovat aplikaci.

### <a name="startupcs"></a>Startup.cs

Webový hostitel vytvořený v *Program.cs* odkazuje na třídu Startup a volá její metody ke konfiguraci aplikace. Metoda ConfigureServices je zodpovědná za nastavení všech služeb, které bude aplikace používat. Metoda `Configure` nastaví kanál požadavků HTTP aplikace. Každý požadavek prochází tímto kanálem, interakci s každým *kusem middleware,* jak to dělá tak.

### <a name="indexcshtml"></a>Soubor Index.cshtml

Domovská stránka webu obsahuje některé značky HTML a některé kód razor na straně serveru. Používá razor k určení modelu `IndexModel`stránky , který je umístěn v *přidruženém souboru Index.cshtml.cs.* Také nastaví název stránky nastavením hodnoty v ViewData. Tato hodnota ViewData se čte v souboru * \_Layout.cshtml,* který se nachází ve složce Sdílené ve složce Stránky. Soubor rozložení je sdílen mnoha Razor stránky a poskytuje společný vzhled a dojem z aplikace. Obsah každé stránky je vykreslen v html souboru rozložení.

## <a name="run-the-application"></a>Spuštění aplikace

Nyní spusťte aplikaci a zobrazte ji v prohlížeči. Aplikaci můžete spustit pomocí **klávesCtrl**+**F5** nebo výběrem **možnosti Ladění** > **spustit bez ladění** z nabídky sady Visual Studio.

## <a name="customize-the-application"></a>Přizpůsobení aplikace

Přidejte vlastnost do souboru *Index.cshtml.cs* a nastavte její `OnGet` hodnotu na aktuální čas v obslužné rutině:

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Nahraďte obsah v `<div>` *Souboru Index.cshtml* touto značkou:

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Spusťte aplikaci znovu. Měli byste vidět, že stránka nyní zobrazuje aktuální čas, ale je to vždy půlnoc! To není správné.

![Visual Studio 2019 ASP.NET základní projekt v prohlížeči](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Ladění aplikace

Přidejte zarážku k metodě, `OnGet` kde `Time` přiřazujeme hodnotu a tentokrát spusťte ladění aplikace.

Spuštění se zastaví na řádku a `DateTime.Today` můžete vidět, že obsahuje datum, ale čas je vždy půlnoc, protože neobsahuje časová data. 

![Visual Studio 2019 ASP.NET základní projekt v prohlížeči](media/vs-2019/vs2019-breakpoint.png)

Změňte jej `DateTime.Now` použít a pokračovat ve spouštění. Nový kód `OnGet` pro by měl být:

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Nyní byste měli vidět skutečný čas serveru v prohlížeči při přechodu do aplikace.

> [!NOTE]
> Výstup se může lišit od obrázku, protože výstupní formát ToShortDateTimeString závisí na aktuální nastavení jazykové verze. Viz třída <xref:System.DateTime.ToShortTimeString>.

![Visual Studio 2019 ASP.NET základní projekt v prohlížeči](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Další kroky

V dalším videu se dozvíte, jak do aplikace přidat podporu dat.

[Kurz: Práce s daty ve vaší aplikaci ASP.NET Core](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Viz také

- [Kurz: Vytvořte webovou aplikaci Razor Pages s ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
