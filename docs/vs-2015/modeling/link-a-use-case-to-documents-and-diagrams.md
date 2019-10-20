---
title: Propojení případu použití s dokumenty a diagramy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c713759a8ea75eed3048469327f962668efa4f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657644"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Propojení případu použití s dokumenty a diagramy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V diagramu případu použití můžete propojit případ použití s jiným diagramem nebo dokumentem. Například můžete propojit případ použití s následujícími diagramy a dokumenty:

- Sekvenční diagram, který ukazuje, jak jsou cíle případu použití realizovány interakcemi uživatelů a systému nebo jeho hlavními součástmi.

- Diagram činnosti, který zobrazuje podrobné akce uživatelů a systému nebo jeho hlavních součástí při provádění případu použití.

- Stránka nebo odstavec OneNotu, který popisuje případ použití podrobně.

- Dokument aplikace Word nebo PowerPointová prezentace, které popisují případ použití podrobně. Tyto dokumenty můžete uchovávat buď v řešení, nebo v umístění přístupném vašemu týmu, jako je například web služby SharePoint.

  Chcete-li propojit případ použití s dokumentem, vytvořte artefakt v diagramu případu použití a připojte k artefaktu případ použití. Ve vlastnostech artefaktu nastavíte cestu k souboru v jiném diagramu nebo dokumentu. Když dvakrát kliknete na artefakt, otevře se druhý diagram nebo dokument.

  K jednotlivým případům použití můžete připojit libovolný počet artefaktů, jak chcete. Artefakty můžete také propojit s jinými druhy elementů v diagramu případu použití.

### <a name="to-open-a-document-associated-with-an-artifact"></a>Otevření dokumentu přidruženého k artefaktu

- V diagramu případu použití poklikejte na obrazec artefaktu.

     Otevře se přidružený dokument.

### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Propojení případu použití s diagramem nebo souborem ve stejném řešení

1. Nakreslete diagram, jako je sekvenční diagram nebo diagram aktivity, a ilustrujte scénář případu použití.

2. Vraťte se do diagramu případu použití.

3. Přetáhněte diagram nebo soubor z Průzkumník řešení do prázdné části diagramu případu použití.

4. Připojte se z artefaktu k případu použití pomocí **závislosti**.

### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Připojení k souboru řešení, například k dokumentu aplikace Word nebo prezentaci aplikace PowerPoint

1. Přidejte dokument do řešení.

    1. Přesuňte dokument aplikace Word do stejné složky systému Windows jako řešení.

    2. V Průzkumník řešení klikněte pravým tlačítkem myši na řešení, přejděte na **Přidat**a pak klikněte na **existující položka**.

    3. Přejděte do dokumentu aplikace Word a klikněte na tlačítko **Přidat**.

         Wordový dokument se zobrazí ve složce řešení v Průzkumník řešení.

2. Přetáhněte dokument aplikace Word z Průzkumník řešení do prázdné části diagramu případu použití.

     Zobrazí se nový artefakt.

3. Připojte se z artefaktu k případu použití pomocí **závislosti**.

### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Připojení ke sdílenému dokumentu, prvku OneNotu nebo webové stránce

1. Získejte adresu URL sdíleného elementu. Může to být například cesta k síťovému souboru začínající na ' \\ \\ ', nebo webová stránka nebo adresa URL SharePointu začínající na ' http://', nebo odkaz na oddíl, stránku nebo odstavec aplikace OneNote začínající na ' OneNote: '.

2. V sadě nástrojů klikněte na **artefakt** a pak klikněte v diagramu případu použití.

3. Vyberte nový artefakt a zadejte nebo vložte adresu URL do vlastnosti **hypertextový odkaz** .

    > [!NOTE]
    > Pokud chcete zadat cestu k souboru, je nejlepší zvolit soubor buď v běžném pracovním prostoru (počínaje "\\ \\"), nebo v rámci řešení sady Visual Studio. Tím se zajistí, že cesta k souboru zůstane platná v počítači jiného člena týmu, nebo pokud je řešení přesunuto. Pokud chcete do řešení přidat dokument, jako je wordový dokument, klikněte pravým tlačítkem na řešení v Průzkumník řešení, přejděte na **Přidat** a pak klikněte na **existující položka**.

## <a name="see-also"></a>Viz také
 [Diagramy případů použití UML: referenční](../modeling/uml-use-case-diagrams-reference.md) [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md) k [úpravám modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md) [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md)
