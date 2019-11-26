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
ms.openlocfilehash: 1df72c6978f5ab34a86c74dbc1ea349db5aa4457
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491303"
---
# <a name="how-to-install-a-visualizer"></a>Postupy: Instalace vizualizéru
Po vytvoření Vizualizér musíte nainstalovat vizualizér, aby byl dostupný v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalace Vizualizátoru je jednoduchý proces.

> [!NOTE]
> V aplikacích pro UWP jsou podporované jenom standardní vizualizace textu, HTML, XML a JSON. Vlastní (uživatelsky vytvořené) vizualizace se nepodporují.

### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Instalace Vizualizér pro Visual Studio 2019
  
1. Vyhledejte knihovnu DLL, která obsahuje vámi sestavený Vizualizér.

2. Zkopírujte knihovnu DLL na [straně ladicího programu](create-custom-visualizers-of-data.md#to-create-the-debugger-side) do některého z následujících umístění:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Zkopírujte [laděného procesuou](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) knihovnu DLL do některého z následujících umístění:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    Kde *Framework* je:
    - `net2.0` pro laděných procesů, na kterém běží modul runtime `.NET Framework`
    - `netstandard2.0` pro laděných procesů pomocí modulu runtime, který podporuje `netstandard 2.0` (`.NET Framework v4.6.1+` nebo `.NET Core 2.0+`).
    - `netcoreapp` pro laděných procesů, na kterém běží modul runtime `.NET Core` (podporuje `.NET Core 2.0+`)

4. Restartujte ladicí relaci.

### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Instalace Vizualizér pro Visual Studio 2017 a starší

> [!IMPORTANT]
> V aplikaci Visual Studio 2017 a starší jsou podporovány pouze .NET Framework vizualizace.

1. Vyhledejte knihovnu DLL, která obsahuje vámi sestavený Vizualizér.

2. Zkopírujte knihovnu DLL do některého z následujících umístění:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Restartujte ladicí relaci.

> [!NOTE]
> Pokud chcete použít spravovaný Vizualizér pro vzdálené ladění, zkopírujte knihovnu DLL do stejné cesty na vzdáleném počítači.

## <a name="see-also"></a>Viz také:
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
- [How to: Write a Visualizer](create-custom-visualizers-of-data.md)
