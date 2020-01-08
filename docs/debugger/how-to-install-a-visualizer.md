---
title: 'Postupy: instalace Vizualizátoru | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b7dfd28d70b80fd2d0f854b7db3550862b32814
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404364"
---
# <a name="how-to-install-a-visualizer"></a>Postupy: Instalace vizualizéru
Po vytvoření Vizualizér musíte nainstalovat vizualizér, aby byl dostupný v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalace Vizualizátoru je jednoduchý proces.

> [!NOTE]
> V aplikacích pro UWP jsou podporované jenom standardní vizualizace textu, HTML, XML a JSON. Vlastní (uživatelsky vytvořené) vizualizace se nepodporují.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Instalace Vizualizér pro Visual Studio 2019
  
1. Vyhledejte knihovnu DLL, která obsahuje vámi sestavený Vizualizér.

2. Zkopírujte soubor DLL na [straně ladicího programu](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (a všechny knihovny DLL, na kterých závisí) do některého z následujících umístění:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Zkopírujte [laděného procesuou](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) knihovnu DLL do některého z následujících umístění:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    kde *Framework* je:
    - `net2.0` pro laděných procesů, na kterém běží modul runtime `.NET Framework`
    - `netstandard2.0` pro laděných procesů pomocí modulu runtime, který podporuje `netstandard 2.0` (`.NET Framework v4.6.1+` nebo `.NET Core 2.0+`).
    - `netcoreapp` pro laděných procesů, na kterém běží modul runtime `.NET Core` (podporuje `.NET Core 2.0+`)

4. Restartujte relaci ladění.

> [!NOTE]
> Postup se liší v aplikaci Visual Studio 2017 a starších. Viz [předchozí verze](how-to-install-a-visualizer.md?view=vs-2017) tohoto článku.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Instalace Vizualizér pro Visual Studio 2017 a starší

> [!IMPORTANT]
> V aplikaci Visual Studio 2017 a starší jsou podporovány pouze .NET Framework vizualizace.

1. Vyhledejte knihovnu DLL, která obsahuje vámi sestavený Vizualizér.

2. Zkopírujte knihovnu DLL do některého z následujících umístění:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Restartujte relaci ladění.

> [!NOTE]
> Pokud chcete použít spravovaný Vizualizér pro vzdálené ladění, zkopírujte knihovnu DLL do stejné cesty na vzdáleném počítači.
::: moniker-end

## <a name="see-also"></a>Viz také:
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
- [How to: Write a Visualizer](create-custom-visualizers-of-data.md)
