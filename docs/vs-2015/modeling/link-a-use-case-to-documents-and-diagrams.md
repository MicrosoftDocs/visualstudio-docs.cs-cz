---
title: Propojení případu použití s dokumenty a diagramy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a5b4ef580825115a1d44c3abb39404332a4277ea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787910"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Propojení případu použití s dokumenty a diagramy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Propojení případu použití v diagramu případu použití do jiného diagramu nebo dokumentu. Můžete například propojit případ použití následující diagramy a dokumenty:  
  
- Sekvenční diagram, který ukazuje, jak se provádí cíle případ použití interakce mezi uživateli a systému nebo jeho hlavní komponenty.  
  
- Diagram aktivity, který zobrazuje podrobné akce uživatelů a systému nebo jeho hlavní komponenty, když provádějí případu použití.  
  
- Stránka Onenotu nebo odstavce, která případ použití podrobně popisuje.  
  
- Dokument aplikace Word nebo prezentace aplikace PowerPoint, která případ použití podrobně popisuje. Abyste mohli tyto dokumenty v řešení, nebo v umístění přístupné pro váš tým, jako je web služby SharePoint.  
  
  K propojení případu použití k dokumentu, vytvoření artefakt v diagramu případu použití a připojení případu použití s artefaktem. V artefaktu se vlastnosti nastavena cesta k souboru diagramu nebo dokumentu. Když dvakrát kliknete na artefakt, další diagram nebo dokument se otevře.  
  
  Protože mnoho artefakty na každý případ použití, jak chcete, aby se můžete připojit. Můžete také propojit s artefakty jiné druhy elementu v diagramu případu použití.  
  
### <a name="to-open-a-document-associated-with-an-artifact"></a>Chcete-li otevřít dokument přidružený k artefakt  
  
-   Na diagramu případu použití dvakrát klikněte na tvar artefaktů.  
  
     Související dokument se otevře.  
  
### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Propojení případu použití diagramu nebo soubor ve stejném řešení  
  
1.  Nakreslení diagramu, jako je například sekvenční diagram nebo aktivita diagram pro ilustraci scénář případu použití.  
  
2.  Přejděte zpět na diagramu případu použití.  
  
3.  Přetáhněte diagram nebo souboru z Průzkumníku řešení na prázdnou část diagramu případu použití.  
  
4.  Připojení z artefaktů k případu použití pomocí **závislost**.  
  
### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Odkaz na soubor řešení například dokument aplikace Word nebo prezentace aplikace PowerPoint  
  
1.  Přidání dokumentu do řešení.  
  
    1.  Přesunete do stejné složky jako řešení Windows Wordový dokument.  
  
    2.  V Průzkumníku řešení klikněte pravým tlačítkem na řešení, přejděte na **přidat**a potom klikněte na tlačítko **existující položku**.  
  
    3.  Přejděte do dokumentu aplikace Word a klikněte na tlačítko **přidat**.  
  
         Dokument aplikace Word se zobrazí ve složce řešení v Průzkumníku řešení.  
  
2.  Dokument aplikace Word přetáhněte z Průzkumníka řešení na prázdnou část diagramu případu použití.  
  
     Zobrazí se nové artefaktů.  
  
3.  Připojení z artefaktů k případu použití pomocí **závislost**.  
  
### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Odkaz na sdílený dokument, OneNote element nebo webové stránky  
  
1.  Získáte adresu URL sdílené elementu. To může být, například na začátku cesty souboru sítě "\\\\", nebo na webové stránce nebo adresa URL Sharepointu začátek 'http://' nebo odkaz na oddíl Onenotu stránce nebo odstavce začátku "onenote:".  
  
2.  Na panelu nástrojů klikněte na tlačítko **artefaktů** a potom klikněte na tlačítko v diagramu případu použití.  
  
3.  S novou artefakt vybrali, zadejte nebo vložte adresu URL do **hypertextový odkaz** vlastnost.  
  
    > [!NOTE]
    >  Pokud chcete zadat cestu k souboru, je nejlepší zvolte soubor, buď v běžné pracovní prostor (počínaje "\\\\"), nebo soubor v rámci řešení sady Visual Studio. Tím se zajistí, že cesta k souboru zůstane v platnosti v počítači jiného člena týmu, nebo pokud se přesune řešení. Chcete-li dokument jako dokument aplikace Word je přidat do vašeho řešení, klikněte pravým tlačítkem na řešení v Průzkumníku řešení, přejděte na **přidat** a potom klikněte na tlačítko **existující položku**.  
  
## <a name="see-also"></a>Viz také  
 [Diagramy případů použití UML: referenční dokumentace](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)   
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)



