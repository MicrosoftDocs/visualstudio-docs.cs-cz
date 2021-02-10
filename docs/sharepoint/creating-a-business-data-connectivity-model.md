---
title: Vytvoření modelu připojení obchodních dat | Microsoft Docs
description: Vytvořte si model služby připojení obchodních dat (BDC) nebo upravte existující model služby BDC pomocí sady Visual Studio. Každý projekt služby SharePoint může obsahovat pouze jeden model.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8232847ce336ca559134aa1211a70057a1306faa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949256"
---
# <a name="create-a-business-data-connectivity-model"></a>Vytvoření modelu připojení obchodních dat
  Můžete vytvořit model služby připojení obchodních dat (BDC) nebo upravit existující model služby BDC pomocí sady Visual Studio. Každý projekt služby SharePoint může obsahovat pouze jeden model. Další informace najdete v tématu [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="create-a-new-model"></a>Vytvořit nový model
 Pokud chcete vytvořit nový model, vytvořte projekt **modelu připojení obchodních dat** nebo přidejte položku **modelu připojení obchodních dat** do **prázdného projektu SharePoint**.

> [!NOTE]
> Musíte mít [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] nainstalovaný na počítači.

 Visual Studio přidá do projektu složku. Tato složka má název, který zadáte pro položku **Model připojení obchodních dat** v dialogovém okně **Přidat novou položku** . Pokud vytvoříte nový projekt **modelu připojení obchodních dat** , Visual Studio pojmenuje složku **BdcModel1**.

 Visual Studio přidá do nové složky následující soubory:

|Soubor|Description|
|----------|-----------------|
|Definiční soubor modelu|Obsahuje kód XML, který definuje entity, metody, obchodní objekty LOB a další metadata, která popisují model.<br /><br /> Upravte metadata v tomto souboru pomocí návrháře služby BDC, okna **Průzkumníka služby BDC**, okna **Podrobnosti metody služby BDC** a okna **vlastností** .|
|Soubor kódu entity Service|Obsahuje metody, které načítají, aktualizují a odstraňují instance výchozí entity.|

 Chcete-li definovat vlastnosti entity, upravte soubor kódu entity. Další informace naleznete v tématu [How to: Add a entity to a model](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Chcete-li načíst, aktualizovat a odstranit instance entity, přidejte kód do souboru kódu entity Service. Další informace najdete v tématu [navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

 Při kompilaci projektu vytvoří Visual Studio sestavení. Ujistěte se, že do projektu nepřidáte další položky, které přidávají kód do sestavení projektu (například: **sekvenční položka pracovního postupu** nebo položka **webové části** ). Kód pro tuto položku se nespustí, když nasadíte řešení, protože balíček řešení nekopíruje sestavení do globální mezipaměti sestavení (GAC).  Balíček řešení nasadí sestavení do databáze služby BDC pouze ve službě SharePoint.

> [!NOTE]
> Visual Studio zkopíruje sestavení do obou umístění v místním počítači při ladění projektu.

## <a name="add-an-existing-model"></a>Přidat existující model
 Model, který byl vytvořen, můžete importovat pomocí jiných nástrojů, jako je například SharePoint Designer. Můžete importovat existující model do projektu v následujících situacích:

- Přizpůsobení modelu, který je již nasazen na serverovou farmu služby SharePoint.

- Zabalení a nasazení existujícího modelu do více SharePoint serverových farem.

  V obou případech nejsou systémy LOB definované v modelu, který importujete, ovlivněné a budou dál fungovat podle očekávání. Chcete-li přidat existující model do projektu služby SharePoint, použijte dialogové okno **Přidat existující položku** aplikace Visual Studio. Další informace najdete v tématu [Postup: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).

  Můžete přidat systém LOB typu .NET Framework sestavení do importovaného modelu výběrem možnosti v **objektu pro přidání sestavení .NET**. To umožňuje napsat vlastní kód a použít návrháře k definování metadat pro importovaný model.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md)|Ukazuje, jak vytvořit nový model služby BDC.|
|[Postupy: Přidání stávajícího souboru modelu služby BDC do projektu služby SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Ukazuje, jak importovat existující model do projektu služby SharePoint.|
|[Postupy: použití souboru prostředků k určení lokalizovaných názvů, vlastností a oprávnění](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Popisuje, jak poskytnout řetězce, které jsou sloučeny s metadaty modelu, když je model spotřebován webovou částí nebo webovou stránkou.|
|[Postupy: Zahrnutí vlastního sestavení ve funkci BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Ukazuje, jak zahrnout vlastní sestavení do funkce.|
