---
title: Prostředí příkazového řádku & výzvy pro vývojáře
description: Začněte z nabídky nástroje > nabídce příkazového řádku. Visual Studio Developer Command Prompt, vývojové prostředí PowerShell a terminál vám umožní snadněji používat nástroje .NET a C++.
author: TerryGLee
ms.author: tglee
ms.date: 06/11/2021
ms.topic: reference
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: fef783475304bb1faa1788bde591a22ed610d528
ms.sourcegitcommit: e7629e132a4d2fad6bb5869e4d68d9dbeeae9631
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2021
ms.locfileid: "113649164"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Visual Studio PowerShell Developer Command Prompt a vývojář

Visual Studio 2019 obsahuje dvě prostředí příkazového řádku pro vývojáře:

- **Visual Studio Developer Command Prompt** – standardní příkazový řádek s některými proměnnými prostředí nastavenými na snadnější použití vývojářských nástrojů příkazového řádku. k dispozici od Visual Studio 2015.

- **Visual Studio PowerShell pro vývojáře** – výkonnější než příkazový řádek. Například můžete předat výstup jednoho příkazu (známého jako *cmdlet* ) do jiného cmdlet . Toto prostředí má stejné proměnné prostředí nastavené jako Developer Command Prompt. k dispozici od Visual Studio 2019.

:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Developer Command Prompt pro Visual Studio zobrazující nástroj clrver":::

od verze Visual Studio 2019 16,5 Visual Studio zahrnuje integrovaný **terminál** , který může hostovat některé z těchto prostředí (Developer Command Prompt a vývojář PowerShell). Můžete také otevřít několik karet každého prostředí. Visual Studio terminál je postaven nad [Terminál Windows](/windows/terminal/). chcete-li otevřít terminál v Visual Studio, klikněte na tlačítko **zobrazit**  >  **terminál**.

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Visual Studio terminálu znázorňující více karet":::

když otevřete některou z vývojářských prostředí z Visual Studio, buď jako samostatnou aplikaci nebo v okně terminálu, se otevře adresář vašeho aktuálního řešení (pokud máte řešení načtené). Díky tomuto chování je vhodné spouštět příkazy proti řešení nebo jeho projektům.

Obě prostředí mají sadu specifických proměnných prostředí, které umožňují snazší použití vývojářských nástrojů příkazového řádku. Po otevření jednoho z těchto prostředí můžete zadat příkazy pro různé nástroje, aniž byste museli znát, kde se nacházejí. 

|Oblíbené příkazy|Description|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Sestavení projektu nebo řešení|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| [nástroj .NET Framework](/dotnet/framework/tools/index) pro CLR|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|[.NET Framework nástroj](/dotnet/framework/tools/index) pro disassembler|
|[`dotnet`](/dotnet/core/tools/dotnet)|[Příkaz rozhraní .NET CLI](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|[Příkaz rozhraní .NET CLI](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|Kompilační nástroj C/C++|
|[`NMAKE`](/cpp/build/reference/running-nmake)|Kompilační nástroj C/C++|
|[`LIB`](/cpp/build/reference/lib-reference)| Nástroj pro sestavení C/C++|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| Nástroj pro sestavení C/C++|


## <a name="start-in-visual-studio"></a>Spustit v Visual Studio

Pomocí těchto kroků otevřete Developer Command Prompt nebo vývojové prostředí PowerShell v rámci Visual Studio:

1. Otevřete sadu Visual Studio.

1. Na řádku nabídek vyberte **nástroje**  >  **příkazového řádku**  >  **Developer Command Prompt** nebo **vývojové prostředí PowerShell**.

   ![Položka nabídky příkazového řádku v Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>spustit z nabídky Windows

dalším způsobem, jak spustit prostředí, je nabídka Start. v závislosti na verzi Visual Studio a dalších sadách sdk a úlohách, které jste nainstalovali, můžete mít několik příkazových výzev. 

### <a name="windows-10"></a>Windows 10

1. na klávesnici vyberte **spustit** ![ Windows klávesu s logem.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) a přejděte k písmenu **v**.

1. rozbalte složku **Visual Studio 2019** .

1. Pro VS 2019 vyberte **Developer Command Prompt pro vs 2019** nebo **vývojové prostředí PowerShell**.

   Alternativně můžete začít zadávat název prostředí do vyhledávacího pole na hlavním panelu a vybrat výsledek, který chcete zobrazit v seznamu výsledků, aby se zobrazily shody hledání.

   ![Animovaný obrázek GIF znázorňující chování hledání na Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. kliknutím na klávesu s logem Windows Windows klávesu s logem na klávesnici otevřete obrazovku **Start** ![ .](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) například na klávesnici.

1. Na obrazovce **Start** stiskněte klávesu **CTRL** a +  otevřete seznam **aplikace** a potom stiskněte klávesu **V**. tím zobrazíte seznam, který obsahuje všechny nainstalované Visual Studio výzvy k příkazu.

1. Pro VS 2019 vyberte **Developer Command Prompt pro vs 2019** nebo **vývojové prostředí PowerShell**.

### <a name="windows-7"></a>Windows 7

1. Zvolte **Start** a potom rozbalte **všechny programy**.

1. vyberte **Visual Studio 2019**  >  **Visual Studio Tools**  >  **Developer Command Prompt pro vs 2019** nebo **Developer PowerShell pro vs 2019**.

   ![Windows 7 nabídka Start pomocí zvýrazněného příkazového řádku](./media/developer-command-prompt-for-vs/windows-7-menu.png)

pokud máte nainstalované jiné sady sdk, například [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), může se zobrazit další příkaz. V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.

## <a name="start-from-file-browser"></a>Spustit z prohlížeče souborů 

zkratky pro prostředí, které jste nainstalovali, jsou obvykle umístěny do složky **nabídky Start** pro Visual Studio, například v *%ProgramData%\Microsoft\ Windows \ \ Menu\Programs\ Visual Studio 2019 \ Visual Studio Tools*. Ale pokud hledání příkazového řádku nepřinese očekávané výsledky, můžete zkusit soubory na svém počítači najít ručně.

### <a name="developer-command-prompt"></a>Developer Command Prompt

vyhledejte název souboru příkazového řádku, který je *VsDevCmd.bat*, nebo do složky Tools for Visual Studio, například *% ProgramFiles (x86)% \ Microsoft Visual Studio \ 2019 \ Community \Common7\Tools* (změny cest podle vaší Visual Studio verze, edice a umístění instalace).

Po umístění souboru příkazového řádku ho otevřete tak, že v normálním okně příkazového řádku zadáte následující příkaz:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

nebo do dialogového okna **spuštění** Windows zadejte následující příkaz:

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> je potřeba upravit cestu tak, aby odpovídala vaší instalaci Visual Studio.

### <a name="developer-powershell"></a>Vývojové prostředí PowerShell

vyhledejte soubor skriptu powershellu s názvem *Launch-VsDevShell.ps1* nebo do složky Tools for Visual Studio, například *% ProgramFiles (x86)% \ Microsoft Visual Studio \ 2019 \ Community \Common7\Tools*. (cesta se mění podle vaší Visual Studio verze, edice a umístění instalace.) po vyhledání souboru powershellu ho spusťte zadáním následujícího příkazu na Windows PowerShell nebo na příkazovém řádku powershellu 6:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

ve výchozím nastavení je vývojář powershellu, který se spustí, nakonfigurovaný pro instalaci Visual Studio, jejíž instalační cesta *Launch-VsDevShell.ps1* soubor je umístěný v.

> [!TIP]
> Aby bylo možné spustit, musí být [zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_execution_policies) nastaveny cmdlet .

## <a name="see-also"></a>Viz také

- [Terminál Windows](/windows/terminal/)
- [.NET Framework – nástroje](/dotnet/framework/tools/index)
- [Použití sady nástrojů Microsoft C++ z příkazového řádku](/cpp/build/building-on-the-command-line)
- [Visual Studio Code uživatelé](https://code.visualstudio.com/docs/cpp/config-msvc#:~:text=To%20open%20the%20Developer%20Command,item%20to%20open%20the%20prompt.)
