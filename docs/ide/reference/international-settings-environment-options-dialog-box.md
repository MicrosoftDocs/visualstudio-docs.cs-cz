---
title: Mezinárodní nastavení v dialogovém okně Možnosti
description: Naučte se, jak pomocí stránky mezinárodní nastavení v části prostředí změnit výchozí jazyk, pokud máte nainstalovanou více než jednu jazykovou verzi integrovaného vývojového prostředí (IDE).
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 37be8d3e5a652bb55b1d71f66c0e9c8ca4cc2f16
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617367"
---
# <a name="options-dialog-box-environment--international-settings"></a>Dialogové okno Možnosti: \> mezinárodní nastavení prostředí

V případě, že máte na počítači nainstalovanou více než jednu jazykovou verzi integrovaného vývojového prostředí (IDE), na stránce mezinárodní nastavení můžete změnit výchozí jazyk. K tomuto dialogovému oknu se dostanete tak, že v nabídce **nástroje** vyberete **Možnosti** a pak zvolíte **mezinárodní nastavení** ze složky **prostředí** .

**Jazyk**

Obsahuje seznam dostupných jazyků pro nainstalované jazykové verze produktu. Pokud se prostředí sdílí s více jazyky produktů nebo instalací smíšeného jazyka produktů, je výběr jazyka změněn na **stejný jako v systému Microsoft Windows**.

> [!CAUTION]
> V systému, v němž je nainstalováno více jazyků, nejsou tímto nastavením ovlivněny Visual C++ nástroje pro sestavení (cl.exe, link.exe, nmake.exe, bscmake.exe a související soubory). Tyto nástroje používají verzi pro poslední nainstalovaný jazyk. Nástroje sestavení pro dříve instalovaný jazyk jsou přepsány, protože nástroje Visual C++ Build nepoužívají model satelitní knihovny DLL.

### <a name="see-also"></a>Viz také

- [Instalace jazykových sad](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
