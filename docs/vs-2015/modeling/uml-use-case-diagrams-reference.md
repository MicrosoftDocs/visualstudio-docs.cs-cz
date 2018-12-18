---
title: 'Diagramy případů použití UML: Referenční | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 64eece28fc46fce799eff01e7ed1e7302e939dbc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791759"
---
# <a name="uml-use-case-diagrams-reference"></a>Diagramy případů použití UML: Referenční dokumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio *diagramu případu použití* shrnuje, kdo používá vaše aplikace nebo systému, a co mohou provádět s ním. Chcete-li vytvořit diagram případu použití UML, na **architektury** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**.  
  
 Diagram případu použití funguje jako předměty pro popis požadavků uživatele. Popisuje relace mezi požadavky uživatelů a hlavní součásti. Nepopisuje zasílání požadavků na podrobně; To lze popsat v samostatných diagramech nebo dokumenty, které lze propojit na každý případ použití. Informace o tom, jak diagramy případů použití vám umožňují pochopit, diskutovat a sdělovat požadavky uživatelů najdete v tématu [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  Toto téma popisuje elementy, které jsou k dispozici v diagramech případů použití. Další informace o tom, jak nakreslit diagramy případů použití, naleznete v tématu [diagramy případu použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md). Další informace o tom, jak vytvořit a kreslit diagramy modelování najdete v tématu [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-use-case-diagrams"></a>Diagramy případů použití čtení  
 Tabulky v následujících částech popisují prvky, které jsou k dispozici na diagram případu použití, spolu s jejich hlavní vlastnosti. Úplný seznam vlastností, naleznete v tématu [diagramy případů použití vlastnosti elementů v UML](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).  
  
### <a name="actors-use-cases-and-subsystems"></a>Objektů actor, případy použití a subsystémů  
 ![Prvky v diagramu případu použití](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
|**Obrazec**|**Element**|**Popis a hlavní vlastnosti**|  
|---------------|-----------------|-----------------------------------------|  
|1|**objekt actor**|Představuje uživatele, organizace nebo externí systém, který spolupracuje s vaší aplikace nebo systému. Prvek "actor" je druh typu.<br /><br /> -   **Cesta k obrázku** – cesta k souboru obrázku, který se má použít místo výchozí ikona objektu actor. Ikona by měl být soubor prostředků v rámci projektu sady Visual Studio.|  
|2|**Případ použití**|Představuje akce prováděné jeden nebo více objektů actor plnění určitého cíle. Případ použití je druh typu.<br /><br /> -   **Témata** -subsystému, ve kterém se zobrazí případu použití.|  
|3|**Přidružení**|Označuje, že prvek "actor" účastní případu použití.|  
|4|**Subsystém nebo komponenty**|V systému nebo aplikace, která pracujete nebo jeho část. Můžou být čímkoli od ve velké síti do jedné třídy v aplikaci.<br /><br /> Případy použití, které systém nebo komponenta podporuje uvnitř jeho obdélník. Může být užitečné zobrazit že některé případy mimo obdélníku, použití vyjasnit vašeho systému.<br /><br /> Subsystém v diagramu případu použití má v podstatě stejný typ jako komponentu v diagramu komponent.<br /><br /> -   **Je vytvořena nepřímo** – Pokud je hodnota false, systém provádí obsahuje jednu nebo více objektů, která přímo odpovídají této subsystému. Při hodnotě true je subsystém konstrukce v návrhu, který se zobrazí v systému provádí pouze prostřednictvím instance jejích částí.|  
  
### <a name="structuring-use-cases"></a>Strukturování případy použití  
 ![Případy použití zahrnout, rozšíření a generalizace](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")  
  
|Obrazec|**Element**|Popis|  
|-----------|-----------------|-----------------|  
|5|**Zahrnout**|Včetně případu použití volání nebo vyvolá zahrnutý jeden. Zahrnutí se používá k zobrazení, jak do menších kroků případu použití přestane fungovat. Případ použití součástí je na konci šipku.<br /><br /> Všimněte si, že diagram nezobrazuje pořadí kroků. Diagram činnosti, sekvenční diagram nebo jiného dokumentu můžete použít k popisu tyto podrobnosti.|  
|6|**Rozšíření**|Rozšíření případu použití přidá cíle a kroky k rozšířenému případu použití. Rozšíření fungovat pouze za určitých podmínek. Na konci šipky je rozšířenému případu použití.<br /><br /> Všimněte si, že diagram nezobrazuje přesné podmínky, za kterých rozšíření použije: můžete zaznamenat tyto komentáře nebo jiného dokumentu.|  
|7|**Dědičnost**|Má vztah specializované a obecné prvku. Zobecněný prvek je na konci šipku.<br /><br /> Případ použití specializované dědí cíle a objektům aktor jeho Generalizace a přidat další specifické cíle a kroky k jejich dosažení.<br /><br /> Specializovaný objekt actor dědí případy použití, atributy a asociace jeho Generalizace a může přidat další.|  
|8|**Závislost**|Označuje, že návrh zdroje, závisí na návrhu cíle.|  
|9|**Komentář**|Použít obecné poznámky přidáte do diagramu.|  
|10|**Artefakt**|Artefakt s odkazem do jiného diagramu nebo dokumentu. Můžete jej vytvořit přetažením souboru z Průzkumníku řešení. Nesmí být propojení se závislostí k libovolnému prvku v diagramu. Artefakt se obvykle používá k propojení případu použití do sekvenčního diagramu, stránka Onenotu, dokument aplikace Word nebo prezentace aplikace PowerPoint, který podrobně popisuje. Dokument může být položka v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení nebo dokumentu do sdíleného umístění, jako je web služby SharePoint.<br /><br /> -   **Hypertextový odkaz**. Adresa URL nebo cesta diagramu nebo dokumentu.<br /><br /> Klikněte dvakrát na artefakt k otevření souboru nebo webovou stránku, na který odkazuje.|  
|11 (není vidět)|**Balíčky**|Případy použití, objekty actor a subsystémy mohou být obsaženy v rámci balíčky. Balíček tvary v diagramu nezobrazí, ale můžete nastavit **LinkedPackage** vlastnosti diagramu. Prvky, které následně vytvořit v diagramu jsou umístěny v rámci balíčku. Další informace najdete v tématu [definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md).|  
  
## <a name="see-also"></a>Viz také  
 [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md)   
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Sekvenční diagramy UML: referenční dokumentace](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy komponent UML: referenční dokumentace](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy komponent UML: Referenční dokumentace](../modeling/uml-component-diagrams-reference.md)



