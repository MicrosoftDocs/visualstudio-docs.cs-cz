---
title: 'Diagramy případů použití UML: referenční informace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbea61c2a26b1dc81487365ef8fc3f320ac95943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657309"
---
# <a name="uml-use-case-diagrams-reference"></a>Diagramy případů použití UML: Referenční dokumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Diagram případu použití* v aplikaci Visual Studio shrnuje, kdo používá vaši aplikaci nebo systém a co s ním může dělat. Chcete-li vytvořit diagram případu použití UML, v nabídce **Architektura** klikněte na **Nový UML nebo Diagram vrstev**.

 Diagram případu použití funguje jako fokus pro popis uživatelských požadavků. Popisuje vztahy mezi požadavky, uživateli a hlavními součástmi. Nepopisuje požadavky podrobněji; Ty mohou být popsány v samostatných diagramech nebo v dokumentech, které lze propojit s každým případem použití. Informace o tom, jak diagramy případu použití vám pomohou pochopit, diskutovat a sdělit potřeby vašich uživatelů, najdete v tématu [model uživatelských požadavků](../modeling/model-user-requirements.md).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Toto téma popisuje prvky, které jsou k dispozici v diagramech případů použití. Další informace o tom, jak kreslit diagramy případů použití, najdete v tématu [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md). Další informace o vytváření a kreslení diagramů modelování najdete v tématu [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-use-case-diagrams"></a>Čtení diagramů případů použití
 Tabulky v následujících částech popisují prvky, které jsou k dispozici v diagramu případu použití, spolu s jejich hlavními vlastnostmi. Úplný seznam vlastností naleznete v tématu [Vlastnosti elementů v diagramech případů použití UML](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).

### <a name="actors-use-cases-and-subsystems"></a>Actors, případy použití a subsystémy
 ![Prvky v diagramu případu použití](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

|**Automatického**|**Element**|**Popis a hlavní vlastnosti**|
|---------------|-----------------|-----------------------------------------|
|první|**Tříd**|Představuje uživatele, organizaci nebo externí systém, který komunikuje s vaší aplikací nebo systémem. Objekt actor je druh typu.<br /><br /> **cesta k obrázku** -    – cesta k souboru obrázku, který má být použit místo výchozí ikony objektu actor. Ikona by měla být soubor prostředků v projektu sady Visual Studio.|
|odst|**Případ použití**|Představuje akce provedené jedním nebo více aktéry při dosahování určitého cíle. Případ použití je druh typu.<br /><br /> -   **předměty** – podsystém, ve kterém se zobrazuje případ použití.|
|3|**Řídí**|Indikuje, že objekt actor se účastní případu použití.|
|4|**Podsystém nebo komponenta**|Systém nebo aplikace, na kterých pracujete, nebo její součást. Může to být cokoli od velké sítě až po jednu třídu v aplikaci.<br /><br /> Případy použití, které systém nebo komponenta podporuje, se zobrazí uvnitř jeho rámečku. Může být užitečné zobrazit některé případy použití mimo obdélník a objasnit rozsah systému.<br /><br /> Podsystém v diagramu případu použití má v podstatě stejný typ jako součást v diagramu komponent.<br /><br /> -   **je nepřímo vytvořena instance** – Pokud je hodnota false, má spuštěný systém jeden nebo více objektů, které přímo odpovídají tomuto subsystému. Je-li nastavena hodnota true, podsystém je konstrukcí ve vašem návrhu, který se zobrazí ve vykonávajícím systému pouze prostřednictvím vytváření instancí svých částí prvků.|

### <a name="structuring-use-cases"></a>Strukturování případů použití
 ![Případy použití s zahrnutím, rozšiřováním a generalizací](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")

|Obrazec|**Element**|Popis|
|-----------|-----------------|-----------------|
|5|**Připojit**|Včetně volání případu použití nebo vyvolání zahrnutého. Zařazení se používá k zobrazení způsobu, jakým se případ použití rozdělí na menší kroky. Zahrnutý případ použití je na konci šipky.<br /><br /> Všimněte si, že diagram nezobrazuje pořadí kroků. K popisu těchto podrobností můžete použít diagram aktivity, sekvenční diagram nebo jiný dokument.|
|6|**Zvětšení**|Případ rozšíření případu použití přidá cíle a kroky do rozšířeného případu použití. Rozšíření provozují pouze za určitých podmínek. Rozšířený případ použití je na konci šipky.<br /><br /> Všimněte si, že diagram nezobrazuje přesné podmínky, za kterých se rozšíření používá: můžete je zaznamenat v komentáři nebo jiném dokumentu.|
|čl|**Dědičnost**|Má vztah k specializovanému a zobecněnému prvku. Zobecněný element je na konci šipky.<br /><br /> Specializovaný případ použití dědí cíle a aktéry jeho Generalizace a může přidat konkrétnější cíle a kroky pro jejich dosažení.<br /><br /> Specializovaný objekt actor dědí případy použití, atributy a přidružení jeho Generalizace a může přidat další.|
|8|**Závislosti**|Označuje, že návrh zdroje závisí na návrhu cíle.|
|9|**Vytvořena**|Slouží k přidání obecných poznámek do diagramu.|
|10pruhový|**Artefaktu**|Artefakt poskytuje odkaz na jiný diagram nebo dokument. Můžete ho vytvořit přetažením souboru z Průzkumník řešení. Může být propojen se závislostí s jakýmkoli jiným prvkem v diagramu. Artefakt se obvykle používá k propojení případu použití s sekvenčním diagramem, stránkou OneNotu, dokumentem aplikace Word nebo prezentací PowerPoint, která to podrobně popisuje. Dokument může být buď položka v řešení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nebo dokument ve sdíleném umístění, jako je například web služby SharePoint.<br /><br /> **hypertextový odkaz**-   . Adresa URL nebo cesta k souboru diagramu nebo dokumentu.<br /><br /> Dvojím kliknutím na artefakt otevřete soubor nebo webovou stránku, na které se odkazuje.|
|11 (nezobrazuje se)|**Zásilk**|Případy použití, objekty actor a subsystémy mohou být obsaženy v balíčcích. Obrazce balíčku se v diagramu nezobrazují, ale můžete nastavit vlastnost **LinkedPackage** diagramu. Prvky, které následně vytvoříte v diagramu, jsou umístěny v rámci balíčku. Další informace najdete v tématu [Definování balíčků a oborů názvů](../modeling/define-packages-and-namespaces.md).|

## <a name="see-also"></a>Viz také
 [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md) pro [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md) [sekvence UML: referenční](../modeling/uml-sequence-diagrams-reference.md) diagramy [tříd](../modeling/uml-class-diagrams-reference.md) UML: referenční diagramy komponent UML: Referenční dokumentace diagramů komponent UML: [](../modeling/uml-component-diagrams-reference.md) [referenční](../modeling/uml-component-diagrams-reference.md) dokumentace
