---
title: Správa prostředků aplikace (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: efe2b176db9f6f22f9e38775d5fc8acad87655ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651387"
---
# <a name="managing-application-resources-net"></a>Správa prostředků aplikace (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soubory prostředků jsou soubory, které jsou součástí aplikace, ale nejsou kompilovány, například soubory ikon nebo zvukové soubory. Vzhledem k tomu, že tyto soubory nejsou součástí procesu kompilace, můžete je změnit, aniž byste museli znovu kompilovat binární soubory. Pokud plánujete lokalizaci aplikace, měli byste použít soubory prostředků pro všechny řetězce a další prostředky, které je potřeba změnit při lokalizaci aplikace.

 Další informace o prostředcích v desktopových aplikacích .NET najdete v tématu [prostředky v aplikacích klasické pracovní plochy](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890). Další informace o prostředcích C++ v aplikacích klasické pracovní plochy najdete v tématu [práce se soubory prostředků](https://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780).

 Aplikace pro Windows Store používají jiný model prostředků z desktopových aplikací. Informace o prostředcích v aplikacích pro Windows Store najdete v tématu [Definování prostředků aplikace](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) na webu Windows Dev Center.

## <a name="working-with-resources"></a>Práce s prostředky
 V projektu spravovaného kódu otevřete okno Vlastnosti projektu (klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte **vlastnosti**, nebo zadejte **Vlastnosti projektu** v okně **Snadné spuštění** nebo zadejte ALT + ENTER do  **Průzkumník řešení** okno). Vyberte kartu **prostředky** . Soubor. resx můžete přidat, pokud projekt ještě neobsahuje, přidat a odstranit různé druhy prostředků a upravovat stávající prostředky.

 Chcete-li zjistit, jak pracovat s prostředky C++ v projektech, přečtěte si téma [Postup: vytvoření prostředku](https://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716).
