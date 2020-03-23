---
title: Správa prostředků aplikace (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e53c3701e31733c54869c71820956d674ed4fb8b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593691"
---
# <a name="manage-application-resources-net"></a>Správa prostředků aplikace (.NET)

Soubory prostředků jsou soubory, které jsou součástí aplikace, ale nejsou kompilovány, například soubory ikon nebo zvukové soubory. Vzhledem k tomu, že tyto soubory nejsou součástí procesu kompilace, můžete je změnit bez nutnosti překompilovat binární soubory. Pokud plánujete lokalizovat aplikaci, měli byste použít soubory prostředků pro všechny řetězce a další prostředky, které je třeba změnit při lokalizaci aplikace.

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac [najdete v tématu Správa prostředků aplikací (Visual Studio pro Mac).](/visualstudio/mac/managing-app-resources)

Další informace o prostředcích v aplikacích pro stolní počítače .NET najdete v tématu [Zdroje informací v aplikacích klasické pracovní plochy](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Práce s prostředky

V projektu spravovaného kódu otevřete okno vlastností projektu. Okno vlastností můžete otevřít buď takto:

- Kliknutí pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a výběrvlastnosti **Properties**
- Zadávání **vlastností projektu** do vyhledávacího pole **Ctrl**+**Q**
- Výběr **možnosti Zadání klávesy**+**Alt** v **Průzkumníku řešení**

Vyberte kartu **Zdroje.** Soubor *Resx* můžete přidat, pokud jej projekt již neobsahuje, přidat a odstranit různé druhy zdrojů a upravit existující zdroje.

## <a name="resources-in-other-project-types"></a>Zdroje v jiných typech projektů

Zdroje jsou spravovány v projektech .NET odlišně než v jiných typech projektů. Další informace o zdrojích v:

- aplikace pro univerzální platformu Windows (UPW), viz [Prostředky aplikací a Systém správy prostředků](/windows/uwp/app-resources/)
- Projekty C++, viz [Práce se soubory zdrojů](/cpp/windows/working-with-resource-files) a [Postup: Vytvoření zdroje](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Viz také

- [Prostředky v aplikacích klasické pracovní plochy (.NET Framework)](/dotnet/framework/resources/index)
- [Správa prostředků aplikací (Visual Studio pro Mac)](/visualstudio/mac/managing-app-resources)
