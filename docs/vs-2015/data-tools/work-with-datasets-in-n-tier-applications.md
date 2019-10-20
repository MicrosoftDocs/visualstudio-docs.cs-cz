---
title: Práce s datovými sadami v n-vrstvých aplikacích | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657816"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Práce s datovými sadami ve vícevrstvých aplikacích
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-vrstvé datové aplikace * jsou aplikace zaměřené na data, které jsou rozdělené do několika logických vrstev (nebo *vrstev*). Jinými slovy: n-vrstvá datová aplikace je aplikace, která je rozdělená na více projektů, s úrovní přístupu k datům, vrstvou obchodní logiky a prezentační vrstvou každého ve vlastním projektu. Další informace najdete v tématu [N-vrstvých datových aplikací – přehled](../data-tools/n-tier-data-applications-overview.md).

 Typové datové sady byly vylepšeny, takže třídy objekty TableAdapter a DataSet lze generovat do diskrétních projektů. Díky tomu je možné rychle oddělit vrstvy aplikace a generovat n-vrstvou datovou aplikaci.

 N-vrstvá podpora v typových datových sadách umožňuje iterativní vývoj architektury aplikace až na n-vrstvý návrh. Také odebere požadavek na ruční oddělení kódu do více než jednoho projektu. Začněte navrhovat datovou vrstvu pomocí Návrhář datových sad. Až budete připraveni přenést architekturu aplikace do n-vrstveného návrhu, nastavte vlastnost **projektu DataSet** objektu DataSet tak, aby generovala třídu DataSet do samostatného projektu.

## <a name="in-this-section"></a>V tomto oddílu
 [Oddělení datových sad a objekty TableAdapter do různých projektů](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) Popisuje, jak přesunout generovanou třídu DataSet mimo projekt, který obsahuje vygenerované třídy TableAdapter a do nového projektu.

 [Přidání kódu do objekty TableAdapter do n-vrstvých aplikací](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Popisuje, jak vygenerovat částečnou třídu, ve které lze přidat kód pro n-vrstvou TableAdapter.

 [Přidávání kódu do datových sad v n-vrstvých aplikacích](../data-tools/add-code-to-datasets-in-n-tier-applications.md) Popisuje, jak vygenerovat částečnou třídu, ve které lze přidat kód pro n-vrstvou datovou sadu.

 [Přidání ověřování do n-vrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md) Popisuje, kde přidat kód, který provádí ověřování při změně dat.

 [Návod: vytvoření N-vrstvých datových aplikací](../data-tools/walkthrough-creating-an-n-tier-data-application.md) Poskytuje podrobné pokyny pro vytvoření typové datové sady a oddělení kódu TableAdapter a datové sady do více projektů.

 [Návod: Přidání ověřování do N-vrstvých datových aplikací](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) Poskytuje podrobné pokyny pro přidání ověřování do aplikace, která byla vytvořena v návodu k datové aplikaci v n-vrstvých aplikacích.

## <a name="reference"></a>Odkaz
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>Související oddíly

- [Přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [N-vrstvé a vzdálené aplikace s LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)