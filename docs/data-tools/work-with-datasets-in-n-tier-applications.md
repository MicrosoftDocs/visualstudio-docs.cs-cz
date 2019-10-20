---
title: Práce s datovými sadami ve vícevrstvých aplikacích
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b96f2e51048216388eea50935a1ced536d8d230b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648035"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Práce s datovými sadami ve vícevrstvých aplikacích

*N-vrstvé datové aplikace* jsou aplikace zaměřené na data, které jsou rozdělené do několika logických vrstev (nebo *vrstev*). Jinými slovy: n-vrstvá datová aplikace je aplikace, která je rozdělená na více projektů, s úrovní přístupu k datům, vrstvou obchodní logiky a prezentační vrstvou každého ve vlastním projektu. Další informace najdete v tématu [N-vrstvých datových aplikací – přehled](../data-tools/n-tier-data-applications-overview.md).

Typové datové sady byly vylepšeny, takže třídy objekty TableAdapter a DataSet lze generovat do diskrétních projektů. Díky tomu je možné rychle oddělit vrstvy aplikace a generovat n-vrstvou datovou aplikaci.

N-vrstvá podpora v typových datových sadách umožňuje iterativní vývoj architektury aplikace až na n-vrstvý návrh. Také odebere požadavek na ruční oddělení kódu do více než jednoho projektu. Začněte navrhovat datovou vrstvu pomocí **Návrhář datových sad**. Až budete připraveni přenést architekturu aplikace do n-vrstveného návrhu, nastavte vlastnost **projektu DataSet** objektu DataSet tak, aby generovala třídu DataSet do samostatného projektu.

## <a name="reference"></a>Odkaz

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Viz také:

- [Přehled N-vrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)
- [Návod: Vytvoření n-vrstvých datových aplikací](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Přidávání kódu do objektů TableAdapter ve vícevrstvých aplikacích](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Přidávání kódu do datových sad ve vícevrstvých aplikacích](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Přidávání ověřování do vícevrstvé datové sady](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Rozdělování datových sad a objektů TableAdapter do různých projektů](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Hierarchická aktualizace](../data-tools/hierarchical-update.md)
- [Nástroje datových sad v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Vytvoření a konfigurace objektů TableAdapter](../data-tools/create-and-configure-tableadapters.md)
- [N-vrstvé a vzdálené aplikace s LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)