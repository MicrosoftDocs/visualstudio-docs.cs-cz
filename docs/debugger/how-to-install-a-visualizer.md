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
ms.openlocfilehash: 3c9c2fa8a8fb300c3b7eb702ae3efd216e17141a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733110"
---
# <a name="how-to-install-a-visualizer"></a>Postupy: Instalace vizualizéru
Po vytvoření Vizualizér musíte nainstalovat vizualizér, aby byl dostupný v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalace Vizualizátoru je jednoduchý proces.

> [!NOTE]
> V aplikacích pro UWP jsou podporované jenom standardní vizualizace textu, HTML, XML a JSON. Vlastní (uživatelsky vytvořené) vizualizace se nepodporují.

### <a name="to-install-a-visualizer"></a>Instalace Vizualizátoru

1. Vyhledejte knihovnu DLL, která obsahuje vámi sestavený Vizualizér.

2. Zkopírujte knihovnu DLL do některého z následujících umístění:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Pokud chcete použít spravovaný Vizualizér pro vzdálené ladění, zkopírujte knihovnu DLL do stejné cesty na vzdáleném počítači.

4. Restartujte ladicí relaci.

## <a name="see-also"></a>Viz také:
- [Vytváření vlastních vizualizérů](../debugger/create-custom-visualizers-of-data.md)
- [How to: Write a Visualizer](/visualstudio/debugger/create-custom-visualizers-of-data)