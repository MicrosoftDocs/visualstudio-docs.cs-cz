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
ms.openlocfilehash: 1815b0efeebf98587fe07384ea0b2c8d1f5e1d90
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "88992365"
---
# <a name="manage-application-resources-net"></a>Správa prostředků aplikace (.NET)

Soubory prostředků jsou soubory, které jsou součástí aplikace, ale nejsou kompilovány, například soubory ikon nebo zvukové soubory. Vzhledem k tomu, že tyto soubory nejsou součástí procesu kompilace, můžete je změnit, aniž byste museli znovu kompilovat binární soubory. Pokud plánujete lokalizaci aplikace, měli byste použít soubory prostředků pro všechny řetězce a další prostředky, které je potřeba změnit při lokalizaci aplikace.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [Správa prostředků aplikace (Visual Studio pro Mac)](/visualstudio/mac/managing-app-resources).

Další informace o prostředcích v aplikacích .NET najdete v tématu [prostředky v aplikacích .NET](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Práce s prostředky

V projektu spravovaného kódu otevřete okno Vlastnosti projektu. Okno vlastností lze otevřít buď pomocí:

- Klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte **vlastnosti** .
- Zadání **vlastností projektu** v poli pro hledání v **kombinaci klávesových zkratek** + **Q**
- Volba **klávesy ALT** + **ENTER** v **Průzkumník řešení**

Vyberte kartu **prostředky** . Soubor *. resx* můžete přidat, pokud projekt ještě neobsahuje, přidat a odstranit různé druhy prostředků a upravovat stávající prostředky.

## <a name="resources-in-other-project-types"></a>Prostředky v jiných typech projektů

Prostředky se spravují jinak v projektech .NET než v jiných typech projektů. Další informace o prostředcích v nástroji:

- Aplikace Univerzální platforma Windows (UWP), informace [o prostředcích aplikací a systému správy prostředků](/windows/uwp/app-resources/)
- Projekty C++, viz [práce se soubory prostředků](/cpp/windows/working-with-resource-files) a [Postupy: vytvoření prostředku](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Viz také

- [Prostředky v aplikacích .NET (.NET Framework)](/dotnet/framework/resources/index)
- [Správa prostředků aplikace (Visual Studio pro Mac)](/visualstudio/mac/managing-app-resources)
