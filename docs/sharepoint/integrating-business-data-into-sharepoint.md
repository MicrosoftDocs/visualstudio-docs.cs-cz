---
title: Integrace obchodních dat do služby SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 06d9e8059db8daa1c27b8c1d5fecc50940b7facb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986392"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrace obchodních dat do služby SharePoint
  Obchodní data můžete integrovat do SharePointu. Obchodní data mohou pocházet z aplikací back-end serveru, například [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel nebo SAP nebo webové služby. Uživatelé můžou obchodní data zobrazovat, přidávat, aktualizovat nebo odstraňovat pomocí externích seznamů nebo Webové části obchodních dat v SharePointu.  Uživatelé mají přístup k těmto datům také offline v aplikaci systém Microsoft Office, jako je například Microsoft Outlook. Další informace najdete v tématu [kde můžete zobrazit externí data](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Pokud chcete integrovat data do služby SharePoint, vytvořte model pro službu připojení obchodních dat (BDC). Služba BDC je aplikace v SharePointu, která ukládá informace o datech v obchodních aplikacích. Další informace najdete v tématu [Služba BDC (Business Data Connectivity)](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Modely v aplikaci Visual Studio
 Modely v aplikaci Visual Studio umožňují psát vlastní kód pro načtení a aktualizaci dat z back-endové zdrojů dat. Data můžete také agregovat z více zdrojů dat. Můžete například zobrazit seznam zákazníků, kteří obsahují data z databáze [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] a webové služby.

 Můžete také importovat modely, které jsou již nasazeny do služby SharePoint. Po importu modelu můžete přidat vlastní kód nebo pouze pomocí sady Visual Studio zabalit a nasadit model do více serverových farem SharePoint. Další informace najdete v tématu [Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Návrh modelu v aplikaci Visual Studio
 Model můžete navrhnout pomocí návrháře a několika oken nástrojů. Při návrhu modelu aplikace Visual Studio generuje model XML modelu. Další informace najdete v tématu [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md).

 Model obsahuje entity a metody.

### <a name="entities"></a>podnikům
 Entita popisuje kolekci polí. Entita může například představovat tabulku v databázi. Entita se zobrazí jako typ externího obsahu v SharePointu. Další informace o typech externího obsahu najdete v tématu [co jsou typy externího obsahu?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Metody
 Metoda umožňuje uživatelům externího typu obsahu provádět akci s poli entity. Například metoda aktualizace může uživatelům umožnit změnu adresy a datum narození zákazníka, kde `Address` a `BirthDate` jsou pole entity `Customer`.

 Visual Studio vygeneruje soubor kódu služby pro každou entitu v modelu. Při přidání metody do modelu aplikace Visual Studio vygeneruje odpovídající metodu v souboru kódu služby. K provedení příslušné úlohy přidejte kód do každé metody. Například pokud přidáte do modelu metodu autora, Visual Studio vygeneruje v souboru kódu služby metodu Creator. Tuto metodu volá Služba BDC, když uživatel klikne na tlačítko **Nová položka** v seznamu, který je založený na modelu. Proto přidejte kód do metody Creator, která přidá nová data do zdroje dat. Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Vytvoření modelu připojení obchodních dat](../sharepoint/creating-a-business-data-connectivity-model.md)|Ukazuje, jak vytvořit nový model nebo importovat model, který exportujete ze SharePointu.|
|[Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)|Vysvětluje, jak navrhnout prvky modelu pomocí nástrojů pro návrh sady Visual Studio.|
|[Kdy použít SharePoint Designer vs. Visual Studio při sestavování řešení pomocí BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Pomůže se rozhodnout, jestli se má použít aplikace Visual Studio, nebo k vytvoření modelu pro službu BDC použít SharePoint Designer.|
