---
title: Nainstalovat Vizualizér | Microsoft Docs
description: Seznamte se s postupem, jak nainstalovat vizualizér, aby byl dostupný pro účely ladění v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 611347acfe48e561653d644097d56d029b6a4fa6
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298254"
---
# <a name="how-to-install-a-visualizer"></a>Postupy: Instalace vizualizéru
Po vytvoření Vizualizér je nutné nainstalovat vizualizér, aby byl dostupný v nástroji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Instalace Vizualizátoru je jednoduchý proces.

> [!NOTE]
> V aplikacích pro UWP jsou podporované jenom standardní vizualizace textu, HTML, XML a JSON. Vlastní (uživatelsky vytvořené) vizualizace se nepodporují.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>instalace vizualizér pro Visual Studio 2019

1. Vyhledejte knihovnu DLL, která obsahuje vámi sestavený Vizualizér.

   Obvykle je nejvhodnější, pokud knihovna DLL na straně ladicího programu a laděného procesu knihovna DLL jako cílovou platformu určují **Libovolný procesor** . Knihovna DLL na straně ladicího programu musí být buď **Libovolný procesor** , nebo **32**. Cílová platforma pro laděného procesu knihovnu DLL by měla odpovídat procesu laděného procesu.

   >[!NOTE]
   > vizualizér na straně ladicího programu je načten v procesu Visual Studio, takže musí být .NET Framework DLL. laděného procesu může být buď .NET Framework, nebo .NET Standard v závislosti na tom, jaký proces se v Visual Studio má ladit.

2. Zkopírujte soubor DLL na [straně ladicího programu](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (a všechny knihovny DLL, na kterých závisí) do některého z následujících umístění:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. Zkopírujte [laděného procesuou](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) knihovnu DLL do některého z následujících umístění:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Rozhraní .NET Framework*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Rozhraní .NET Framework*

    kde *Framework* je:
    - `net2.0` pro laděných procesů, který spouští `.NET Framework` modul runtime.
    - `netstandard2.0` pro laděných procesů pomocí modulu runtime, který podporuje `netstandard 2.0` ( `.NET Framework v4.6.1+` nebo `.NET Core 2.0+` ).
    - `netcoreapp` pro laděných procesů, který spouští `.NET Core` modul runtime. (podporuje `.NET Core 2.0+` )

   Laděného procesu knihovna DLL je nutná, pokud chcete vytvořit samostatný Vizualizér. Tato knihovna DLL obsahuje kód pro datový objekt, který může implementovat metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

   Pokud pro laděného procesu kód cílíte na více platforem, musí být knihovna DLL laděného procesu umístěna do složky pro minimální podporované TFM.

4. Restartujte ladicí relaci.

> [!NOTE]
> postup se liší v Visual Studio 2017 a starších. Viz [předchozí verze](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) tohoto článku.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>instalace vizualizér pro Visual Studio 2017 a starší

> [!IMPORTANT]
> v Visual Studio 2017 a starších se podporují jenom .NET Framework vizualizace.

1. Vyhledejte knihovnu DLL, která obsahuje vámi sestavený Vizualizér.

2. Zkopírujte knihovnu DLL do některého z následujících umístění:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. Restartujte ladicí relaci.

> [!NOTE]
> Pokud chcete použít spravovaný Vizualizér pro vzdálené ladění, zkopírujte knihovnu DLL do stejné cesty na vzdáleném počítači.
::: moniker-end

## <a name="see-also"></a>Viz také
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
- [Postupy: Zápis vizualizéru](create-custom-visualizers-of-data.md)
