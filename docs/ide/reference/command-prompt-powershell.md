---
title: Prostředí příkazového řádku & výzvy pro vývojáře
description: Začněte z nabídky nástroje > nabídce příkazového řádku. Visual Studio Developer Command Prompt, vývojové prostředí PowerShell a terminál vám umožní snadněji používat nástroje .NET a C++.
ms.date: 04/11/2021
ms.custom: contperf-fy21q4
helpviewer_keywords:
- Visual Studio command prompt
- command prompt, Visual Studio
- Developer Command Prompt
- Developer PowerShell
- Visual Studio terminal
ms.assetid: 94fcf524-9045-4993-bfb2-e2d8bad44219
no-loc: cmdlet
ms.openlocfilehash: 57cbc93f4b6e8cf64dd5149462788e0cde833350
ms.sourcegitcommit: 52b093e000334f53d87c6165d1418347e4f45dec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2021
ms.locfileid: "107221728"
---
# <a name="visual-studio-developer-command-prompt-and-developer-powershell"></a>Visual Studio Developer Command Prompt a vývojové prostředí PowerShell

Visual Studio 2019 obsahuje dvě prostředí příkazového řádku pro vývojáře:

- **Visual Studio Developer Command Prompt** – standardní příkazový řádek s určitými proměnnými prostředí nastavenými na snadnější použití vývojářských nástrojů příkazového řádku. K dispozici od aplikace Visual Studio 2015.

- **PowerShell pro vývojáře sady Visual Studio** – výkonnější než příkazový řádek. Například můžete předat výstup jednoho příkazu (známého jako *cmdlet* ) do jiného cmdlet . Toto prostředí má stejné proměnné prostředí nastavené jako Developer Command Prompt. K dispozici od aplikace Visual Studio 2019.


:::image type="content" source="media/developer-command-prompt-for-vs/command-prompt.png" alt-text="Developer Command Prompt pro Visual Studio zobrazující nástroj Clrver":::

Počínaje verzí Visual Studio 2019 verze 16,5 obsahuje Visual Studio integrovaný **terminál** , který může hostovat některé z těchto prostředí (Developer Command Prompt a vývojové prostředí PowerShell). Můžete také otevřít několik karet každého prostředí. Terminál sady Visual Studio je postaven na [terminálu Windows](/windows/terminal/). Chcete-li otevřít terminál v aplikaci Visual Studio, klikněte na tlačítko **Zobrazit**  >  **terminál**.

:::image type="content" source="media/developer-command-prompt-for-vs/vs-terminal.png" alt-text="Terminál sady Visual Studio zobrazující více karet":::

Když otevřete některou z vývojářských prostředí ze sady Visual Studio, ať už jako samostatnou aplikaci nebo v okně terminálu, otevře se v adresáři aktuálního řešení (Pokud máte řešení načtené). Díky tomuto chování je vhodné spouštět příkazy proti řešení nebo jeho projektům.

Obě prostředí mají sadu specifických proměnných prostředí, které umožňují snazší použití vývojářských nástrojů příkazového řádku. Po otevření jednoho z těchto prostředí můžete zadat příkazy pro různé nástroje, aniž byste museli znát, kde se nacházejí. 

|Oblíbené příkazy|Description|
|--|--|
|[`MSBuild`](../../msbuild/msbuild-command-line-reference.md)|Sestavení projektu nebo řešení|
|[`clrver`](/dotnet/framework/tools/clrver-exe-clr-version-tool)| [.NET Framework nástroje](/dotnet/framework/tools/index) pro CLR.|
|[`ildasm`](/dotnet/framework/tools/ildasm-exe-il-disassembler)|[.NET Framework nástroj](/dotnet/framework/tools/index) pro Disassembler|
|[`dotnet`](/dotnet/core/tools/dotnet)|[Příkaz rozhraní .NET CLI](/dotnet/core/tools/index)|
|[`dotnet run`](/dotnet/core/tools/dotnet-run)|[Příkaz rozhraní .NET CLI](/dotnet/core/tools/index)|
|[`CL`](/cpp/build/reference/compiler-command-line-syntax)|Kompilační nástroj C/C++|
|[`NMAKE`](/cpp/build/reference/running-nmake)|Kompilační nástroj C/C++|
|[`LIB`](/cpp/build/reference/lib-reference)| Nástroj pro sestavení C/C++|
|[`DUMPBIN`](/cpp/build/reference/dumpbin-reference)| Nástroj pro sestavení C/C++|


## <a name="start-in-visual-studio"></a>Spustit v aplikaci Visual Studio

Pomocí těchto kroků otevřete Developer Command Prompt nebo vývojové prostředí PowerShell v rámci sady Visual Studio:

1. Otevřete sadu Visual Studio.

1. Na řádku nabídek vyberte **nástroje**  >  **příkazového řádku**  >  **Developer Command Prompt** nebo **vývojové prostředí PowerShell**.

   ![Položka nabídky příkazového řádku v aplikaci Visual Studio](./media/developer-command-prompt-for-vs/vs-menu.png)

## <a name="start-from-windows-menu"></a>Spustit z nabídky systému Windows

Další způsob, jak spustit prostředí, je z nabídky Start. V závislosti na verzi sady Visual Studio a všech dalších sadách SDK a úlohách, které jste nainstalovali, může být více příkazů. 

### <a name="windows-10"></a>Windows 10

1. Na klávesnici vyberte **Spustit** ![ klávesu s logem Windows.](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) a přejděte k písmenu **v**.

1. Rozbalte složku **Visual Studio 2019** .

1. Pro VS 2019 vyberte **Developer Command Prompt pro vs 2019** nebo **vývojové prostředí PowerShell**.

   Alternativně můžete začít zadávat název prostředí do vyhledávacího pole na hlavním panelu a vybrat výsledek, který chcete zobrazit v seznamu výsledků, aby se zobrazily shody hledání.

   ![Animovaný obrázek GIF znázorňující chování hledání ve Windows 10](./media/developer-command-prompt-for-vs/windows-10-search.gif)

### <a name="windows-81"></a>Windows 8.1

1. Kliknutím na klávesu s logem Windows na klávesnici na obrazovce Start přejdete na **úvodní** obrazovku ![ .](./media/developer-command-prompt-for-vs/windows-logo-key-graphic.png) například na klávesnici.

1. Na obrazovce **Start** stiskněte klávesu **CTRL** a +  otevřete seznam **aplikace** a potom stiskněte klávesu **V**. Tím zobrazíte seznam, který obsahuje všechny nainstalované příkazy sady Visual Studio.

1. Pro VS 2019 vyberte **Developer Command Prompt pro vs 2019** nebo **vývojové prostředí PowerShell**.

### <a name="windows-7"></a>Windows 7

1. Zvolte **Start** a potom rozbalte **všechny programy**.

1. Vyberte **Visual Studio 2019**  >  **Visual Studio Tools**  >  **Developer Command Prompt pro vs 2019** nebo **Developer PowerShell pro vs 2019**.

   ![Nabídka Start ve Windows 7 se zvýrazněným příkazovým řádkem](./media/developer-command-prompt-for-vs/windows-7-menu.png)

Pokud máte nainstalované jiné sady SDK, jako je například [Sada Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) nebo [předchozí verze](https://developer.microsoft.com/windows/downloads/sdk-archive), může se zobrazit další příkazová výzva. V dokumentaci pro jednotlivé nástroje zjistíte, kterou verzi příkazového řádku byste měli použít.

## <a name="start-from-file-browser"></a>Spustit z prohlížeče souborů 

Obvykle jsou zástupci pro prostředí, které jste nainstalovali, umístěny do složky **nabídky Start** pro Visual Studio, jako je například v *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual studiu 2019 \ Visual Studio Tools*. Ale pokud hledání příkazového řádku nepřinese očekávané výsledky, můžete zkusit soubory na svém počítači najít ručně.

### <a name="developer-command-prompt"></a>Developer Command Prompt

Vyhledejte název souboru příkazového řádku, který je *VsDevCmd.bat*, nebo přejít do složky Tools for Visual Studio, například *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools* (cesta se mění podle verze sady Visual Studio, edice a umístění instalace).

Po umístění souboru příkazového řádku ho otevřete tak, že v normálním okně příkazového řádku zadáte následující příkaz:

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

Nebo v dialogovém okně **spuštění** systému Windows zadejte následující příkaz:

```cmd
%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat"
```

> [!TIP]
> Budete muset upravit cestu tak, aby odpovídala vaší instalaci sady Visual Studio.

### <a name="developer-powershell"></a>Vývojové prostředí PowerShell

Vyhledejte soubor skriptu PowerShellu s názvem *Launch-VsDevShell.ps1* nebo do složky Tools for Visual Studio, například *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\Community\Common7\Tools*. (Cesta se mění podle vaší verze, edice a umístění sady Visual Studio.) Po vyhledání souboru PowerShellu ho spusťte zadáním následujícího příkazu na příkazovém řádku Windows PowerShellu nebo PowerShellu 6:

```powershell
& 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\Launch-VsDevShell.ps1'
```

Ve výchozím nastavení je prostředí PowerShell pro vývojáře, které se spouští, nakonfigurované pro instalaci sady Visual Studio, jejíž cesta k instalaci *Launch-VsDevShell.ps1* soubor je umístěný v.

> [!TIP]
> Aby bylo možné spustit, musí být [zásady spouštění](/powershell/module/microsoft.powershell.core/about/about_execution_policies) nastaveny cmdlet .

## <a name="see-also"></a>Viz také

- [Vývojové prostředí PowerShell](https://devblogs.microsoft.com/visualstudio/the-powershell-you-know-and-love-now-with-a-side-of-visual-studio/)
- [Řekněte Hello novému terminálovému terminálu pro Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)
- [Terminál Windows](/windows/terminal/)
- [.NET Framework – nástroje](/dotnet/framework/tools/index)
- [Správa externích nástrojů](../managing-external-tools.md)
- [Použití sady nástrojů Microsoft C++ z příkazového řádku](/cpp/build/building-on-the-command-line)
