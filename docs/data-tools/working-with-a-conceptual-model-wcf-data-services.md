---
title: Práce s koncepčním modelem (Datové služby WCF)
description: Práce s koncepčním modelem v Datové služby WCF. Dotazujte data prostřednictvím objektů místo překládání mezi schématy databáze a objektovými modely.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ef5745f974848da75b4dcc0c42b59b38aa61cd0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866109"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Práce s koncepčním modelem (Datové služby WCF)

Když použijete koncepční model k popisu dat v databázi, můžete zadávat dotazy na data prostřednictvím objektů, aniž byste museli překládat mezi schématem databáze a objektovým modelem.

Můžete použít koncepční modely s aplikacemi Datové služby WCF. Následující témata ukazují, jak zadávat dotazy na data pomocí koncepčního modelu.

| Téma | Description |
| - | - |
| [Postupy: spouštění dotazů datové služby](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Ukazuje, jak zadávat dotazy na datovou službu z aplikace .NET. |
| [Postupy: výsledky dotazu na projekt](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Ukazuje, jak omezit množství dat vrácených prostřednictvím dotazu datové služby. |

Když použijete koncepční model, můžete definovat, jaký druh dat je platný v jazyce, který odpovídá vaší doméně. V modelu můžete definovat platná data nebo můžete přidat ověřování do operací, které provádíte v entitě nebo datové službě.

Následující témata ukazují, jak přidat ověřování do Datové služby WCF aplikací.

|Téma|Description|
|-----------|-----------------|
|[Postupy: zachycení zpráv datových služeb](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Ukazuje, jak přidat ověřování do operace datové služby.|

 V následujících tématech se dozvíte, jak vytvářet, aktualizovat a odstraňovat data prováděním operací s entitami.

|Téma|Description|
|-----------|-----------------|
|[Postupy: Přidání, úpravy a odstranění entit](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Ukazuje, jak vytvořit, aktualizovat a odstranit data entity v datové službě.|
|[Postupy: definování vztahů mezi entitami](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Ukazuje, jak vytvořit nebo změnit relace v datové službě.|

## <a name="see-also"></a>Viz také

- [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Dotazování v datové službě](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)
