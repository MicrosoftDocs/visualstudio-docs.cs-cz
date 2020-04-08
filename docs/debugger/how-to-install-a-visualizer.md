---
title: 'Postup: Instalace vizualizéru | Dokumenty společnosti Microsoft'
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
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880257"
---
# <a name="how-to-install-a-visualizer"></a>Postupy: Instalace vizualizéru
Po vytvoření vizualizéru je nutné vizualizér [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nainstalovat tak, aby byl k dispozici v aplikaci . Instalace vizualizéru je jednoduchý proces.

> [!NOTE]
> V aplikacích UPW jsou podporovány pouze standardní vizualizéry textu, HTML, XML a JSON. Vlastní vizualizéry (vytvořené uživatelem) nejsou podporovány.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Instalace vizualizéru pro Visual Studio 2019
  
1. Vyhledejte dll, která obsahuje vizualizér, který jste vytvořili.

   Obvykle je nejlepší, pokud dll ladicího programu a ladicí dll zadat **libovolný procesor** jako cílovou platformu. DLL na straně ladicího programu musí být **Libovolný procesor** nebo **32bitová**. Cílová platforma pro dll na straně ladění by měla odpovídat procesu debugee.

2. Zkopírujte knihovnu DLL [na straně ladicího programu ladicího programu](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (a všechny knihovny DLL, na kterých závisí) do některého z následujících umístění:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`
    
3. Zkopírujte dll dll na [straně ladění ladění](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) do některého z následujících umístění:

    - *Rozhraní VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\`*Rozhraní VisualStudioVersion* `\Visualizers\` *Framework*

    kde *framework* je buď:
    - `net2.0`pro ladicí spouštění `.NET Framework` runtime.
    - `netstandard2.0`pro ladicí zařízení pomocí runtime, který podporuje `netstandard 2.0` (`.NET Framework v4.6.1+` nebo `.NET Core 2.0+`).
    - `netcoreapp`pro ladicí spouštění `.NET Core` runtime. (podporuje) `.NET Core 2.0+`

4. Restartujte relaci ladění.

> [!NOTE]
> Postup se liší v sadě Visual Studio 2017 a starší. Podívejte se na [předchozí verzi](how-to-install-a-visualizer.md?view=vs-2017) tohoto článku.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Instalace vizualizéru pro Visual Studio 2017 a starší

> [!IMPORTANT]
> Pouze vizualizéry rozhraní .NET Framework jsou podporovány v sadě Visual Studio 2017 a starší.

1. Vyhledejte dll, která obsahuje vizualizér, který jste vytvořili.

2. Zkopírujte dll do některého z následujících umístění:

    - *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`

    - `My Documents\`*VisualStudioVersion*`\Visualizers`

3. Restartujte relaci ladění.

> [!NOTE]
> Pokud chcete použít spravovaný vizualizér pro vzdálené ladění, zkopírujte dll na stejnou cestu ve vzdáleném počítači.
::: moniker-end

## <a name="see-also"></a>Viz také
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
- [Postupy: Zápis vizualizéru](create-custom-visualizers-of-data.md)
