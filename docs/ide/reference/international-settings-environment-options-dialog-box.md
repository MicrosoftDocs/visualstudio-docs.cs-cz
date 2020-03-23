---
title: Mezinárodní nastavení, prostředí, dialogové okno Možnosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1526e1c49636f4883392caa63966714625d066d6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595511"
---
# <a name="options-dialog-box-environment--international-settings"></a>Dialogové okno Možnosti: Mezinárodní nastavení prostředí \>

Stránka Mezinárodní nastavení umožňuje změnit výchozí jazyk, pokud máte v počítači nainstalovanou více než jednu jazykovou verzi integrovaného vývojového prostředí (IDE). K tomuto dialogovému oknu se dostanete tak, že vyberete **možnosti** z nabídky **Nástroje** a pak zvolte **Mezinárodní nastavení** ze složky **Prostředí.**

**Jazyk**

Zobrazí seznam dostupných jazyků pro nainstalované jazykové verze produktu. Pokud prostředí sdílí více jazyků produktů nebo instalace produktů ve smíšeném jazyce, změní se výběr jazyka na **Stejný jako systém Microsoft Windows**.

> [!CAUTION]
> V systému s nainstalovaným více jazyky nejsou nástroje pro sestavení jazyka Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe a související soubory) tímto nastavením ovlivněny. Tyto nástroje používají verzi pro poslední nainstalovaný jazyk. Nástroje sestavení pro dříve nainstalovaný jazyk jsou přepsány, protože nástroje pro sestavení visual c++ nepoužívají model satelitní dll.

### <a name="see-also"></a>Viz také

- [Instalace jazykových sad](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
