---
title: Navrhování modelu připojení obchodních dat | Microsoft Docs
description: Navrhněte model připojení obchodních dat (BDC). Přidejte entity a metody. Definujte parametry metody. Přidejte popisovače filtru. Ověřte model služby BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fb1aa194688533855b7c5bd1d58a4e3b97ac749
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948839"
---
# <a name="design-a-business-data-connectivity-model"></a>Návrh modelu připojení obchodních dat
  Můžete vyvíjet model pro službu připojení obchodních dat (BDC) přidáním entit a metod do souboru modelu. Entita popisuje kolekci datových polí. Entita může například představovat tabulku v databázi. Metoda provádí úlohu, jako je například přidání, odstranění nebo aktualizace dat reprezentovaných entitami. Další informace najdete v tématu [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Přidání entit
 Entitu můžete přidat přetažením nebo zkopírováním **entity** z **panelu nástrojů** sady Visual Studio do návrháře služby BDC. Další informace naleznete v tématu [How to: Add a entity to a model](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Definujte pole entity ve třídě. Například je možné přidat pole s názvem `Address` do `Customer` třídy. Můžete buď přidat novou třídu do projektu, nebo použít existující třídu vytvořenou pomocí jiných nástrojů, jako je například Návrhář relací objektů (Návrhář O/R). Název entity a název třídy, která představuje entitu, se nemusí shodovat. Třídu můžete při definování metod v modelu spojovat s entitou.

## <a name="add-methods"></a>Přidat metody
 Služba BDC volá metody v modelu, když uživatelé zobrazují, přidávají, aktualizují nebo odstraňují informace v seznamu nebo webové části, která je založená na vašem modelu. Do modelu je nutné přidat metodu pro každý úkol, který může uživatel provádět. Metody vytvoříte tak, že vyberete libovolný z pěti základních typů metod z okna **Podrobnosti metody služby BDC** . Následující tabulka popisuje pět základních metod modelu služby BDC.

|Metoda|Popis|
|------------|-----------------|
|Nález|Vrátí kolekci instancí entit. Volá se, když uživatel otevře seznam nebo webovou část. Další informace najdete v tématu [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md).|
|specifická metoda Finder|Vrátí konkrétní instanci entity. Volá se, když uživatel zobrazí podrobnosti konkrétní položky v seznamu. Další informace najdete v tématu [Postup: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md).|
|tvůrce|Přidá nová data do zdroje dat entity. Volá se, když uživatel vybere tlačítko **Nová položka** na pásu karet seznamu, který je založený na modelu. Další informace naleznete v tématu [How to: Add a Creator Method](../sharepoint/how-to-add-a-creator-method.md).|
|aktualizační metoda|Upraví data v seznamu. Volá se, když uživatelé aktualizují informace v seznamu. Další informace naleznete v tématu [How to: Add a The aktualizační metoda](../sharepoint/how-to-add-an-updater-method.md).|
|metoda odstranění|Odebere data. Volá se, když uživatelé odstraní položku ze seznamu. Další informace naleznete v tématu [How to: Add a deleteer Method](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Definovat parametry metody
 Když vytvoříte metodu, Visual Studio přidá vstupní a výstupní parametry, které jsou vhodné pro typ metody. Tyto parametry jsou pouze zástupné symboly. Ve většině případů je nutné parametry upravit tak, aby předávaly nebo vracely správný typ dat. Například ve výchozím nastavení vrátí vyhledávací metoda řetězec. Ve většině případů chcete změnit návratový parametr vyhledávací metody tak, aby vracela kolekci entit. To lze provést úpravou popisovače typu parametru. Deskriptor typu je kolekce atributů, které popisují datový typ parametru. Další informace naleznete v tématu [How to: define a Type deskriptor parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Visual Studio umožňuje kopírovat popisovače typů mezi parametry v modelu. Například můžete definovat popisovač typu s názvem `CustomerTD` pro návratový parametr `GetCustomer` metody. Popisovač typu můžete zkopírovat `CustomerTD` v **Průzkumníkovi služby BDC** a pak tento popisovač typu vložit do vstupního parametru `CreateCustomer` metody. Tím zabráníte v nutnosti definovat stejný deskriptor typu více než jednou.

## <a name="method-instances"></a>Instance metody
 Když vytvoříte metodu, Visual Studio přidá instanci výchozí metody. Instance metody je odkaz na metodu a navíc výchozí hodnoty pro parametry. Jedna metoda může mít více instancí metod. Každá instance je kombinací signatury metody a sady výchozích hodnot. Další informace naleznete v tématu [How to: define a Type deskriptor parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Při spuštění projektu se instance metody zobrazí v rozevíracím seznamu nad seznamem služby SharePoint. Uživatelé mohou zvolit instance metody pro zobrazení dat.

 Chcete-li přidat výchozí hodnoty do instance metody, je nutné upravit XML modelu přímo. Další informace najdete v tématu [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Přidat deskriptory filtru
 Uživatelé modelu mohou chtít načíst instance entity, které odpovídají určitým kritériím. Chcete-li povolit tuto funkci, můžete přidat popisovač filtru k metodě. Deskriptory filtru umožňují uživatelům modelu filtrovat sady výsledků metod předáním hodnot do metod před jejich spuštěním. Další informace najdete v tématu [Postupy: Přidání parametrů filtru k operacím pro omezení instancí z externího systému](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 SharePoint nabízí několik funkcí, které uživatelům umožňují zadat hodnoty filtru. Například obchodní data Webové části poskytují textové pole filtru. Uživatelé mohou omezit data v seznamu zadáním hodnoty do textového pole. Další informace o tom, jak přidat popisovač filtru do metody, naleznete v tématu [How to: Add a Filter Filter to the Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Vlastnosti popisovače filtru
 Je nutné nastavit hodnotu **přidruženého popisovače typu**, **název** a vlastnosti **typu** popisovače filtru. Všechny ostatní vlastnosti jsou volitelné.

 **Přidružená vlastnost popisovače typu** souvisí s popisovačem filtru na vstupní parametr. Když uživatel zadá hodnotu filtru, Služba BDC tuto hodnotu předává do metody pomocí vstupního parametru.

 Vlastnost **Type** popisuje vzor filtrování, který chcete použít. Ve službě SharePoint má vybraný vzor filtrování vliv na text, který se zobrazí v uživatelském rozhraní (UI). Například pro vzor filtrování komparátor se text **rovná** se jako ovládací prvek nad webovou částí obchodní data. Další informace o jednotlivých vzorech filtrování najdete v tématu [typy filtrů podporované službou BDC](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

 Další informace o vlastnostech popisovače filtru naleznete v tématu [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Zadat výchozí hodnoty
 V některých případech nemusí uživatel poskytovat hodnotu filtru. Můžete zadat výchozí hodnotu přidáním výchozí hodnoty do instance metody nebo nastavením výchozí hodnoty v kódu metody. Další informace o tom, jak přidat výchozí hodnotu do instance metody, naleznete v tématu [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Příklad, jak nastavit výchozí hodnotu vstupního parametru v kódu metody, naleznete v tématu [How to: Add a Filter Filter to the Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Ověření modelu
 Během vývoje můžete model ověřit. Visual Studio identifikuje problémy, které můžou zabránit tomu, aby se model choval podle očekávání. Tyto problémy se zobrazí ve **Seznam chyb** sady Visual Studio.

 Model můžete ověřit tak, že otevřete místní nabídku pro návrháře služby BDC a pak zvolíte **ověřit**. Pokud model obsahuje nějaké chyby, zobrazí se v **Seznam chyb**. Kurzor můžete rychle přesunout do kódu, který obsahuje chybu, dvojitým kliknutím na chybu v seznamu. Jako alternativu můžete zvolit klávesy **F8** nebo **SHIFT** +  opakovaně, abyste mohli procházet chyby v seznamu a předávat je dál.

 Chyby ověřování se můžou vyskytnout, když pravidla modelu porušují nějaký způsob. Pokud je například vlastnost **IsCollection** popisovače typu nastavená na **hodnotu true**, ale neexistují žádné deskriptory podřízeného typu, zobrazí se chyba ověřování. Možná budete muset odkazovat na pravidla modelu služby BDC, abyste porozuměli chybám, které se zobrazí v **Seznam chyb** sady Visual Studio. Další informace o pravidlech modelu služby BDC najdete v tématu [BDCMetadata Schema](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Ladění řešení, které obsahuje model
 Svůj kód můžete ladit, protože byste mohli ladit libovolný kód v aplikaci Visual Studio. Chcete-li ladit kód, nastavte zarážky kdekoli v kódu a poté spusťte ladicí program. Visual Studio otevře web služby SharePoint. V SharePointu vytvořte seznam nebo webovou část, která používá vaše firemní data. Pak můžete krokovat kód. Další informace o ladění projektů SharePoint naleznete v tématu [Poradce při potížích s řešeními služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Můžete také ladit kód ve vlastních sestaveních, která přidáte do projektu. Chcete-li však ladit kód ve vlastním sestavení, je nutné přidat sestavení do balíčku řešení. Další informace najdete v tématu [Postup: Přidání a odebrání dalších sestavení](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Další informace o přidání vlastního sestavení do projektu naleznete v tématu [How to: include a Custom Assembly in a funkce BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).

### <a name="configure-bdc-security"></a>Konfigurace zabezpečení služby BDC
 Než budete moct řešení ladit, možná budete muset změnit nastavení zabezpečení na SharePointu. Chcete-li změnit tato nastavení, otevřete aplikaci služby připojení obchodních dat na webu centrální správy služby SharePoint 2010. V dialogovém okně **nastavit oprávnění úložiště metadat** přidejte svůj uživatelský účet a pak vyberte některou z následujících možností:

|Úkol|Možnost|
|----------|------------|
|Nasazení modelů do služby BDC.|Upravit|
|K vytváření seznamů a Webové části pomocí externích typů obsahu (entity) v modelu.|Vybratelné v klientech|
|K vytváření, čtení, aktualizaci a odstraňování dat entit.|Spuštěním|

 Další informace o těchto nastaveních najdete v tématu [Správa služby připojení obchodních dat](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14)).

 Můžete také nastavit oprávnění zabezpečení pro jednotlivé modely nebo typy externího obsahu. Další informace o tom, jak nastavit oprávnění zabezpečení pro model, najdete v tématu [Správa modelů služby BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)). Další informace o tom, jak nastavit oprávnění zabezpečení externího typu obsahu, najdete v tématu [Správa typů externího obsahu](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14)).

> [!NOTE]
> Pomocí těchto nastavení můžete ladit řešení na místním serveru SharePoint. Další informace o tom, jak nakonfigurovat nastavení zabezpečení služby BDC na provozním serveru služby SharePoint, najdete v tématu [Přehled zabezpečení obchodních dat služby](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14)).

### <a name="retract-models-that-become-corrupt"></a>Odvolat modely, které se stanou poškozeny
 Při prvním spuštění ladicího programu Visual Studio nasadí celý model do služby SharePoint. V každém okamžiku Visual Studio aktualizuje model ve službě SharePoint o všechny změny, které provedete mezi nasazeními.

 Mohou nastat situace, kdy chcete, aby aplikace Visual Studio zcela odvolána model ze SharePointu. Model může být například poškozený.  Chcete-li model znovu nasadit do služby SharePoint, nastavte vlastnost **přírůstkové aktualizace** modelu na **hodnotu NEPRAVDA** a spusťte ladicí program. Vlastnost **přírůstková aktualizace** se zobrazí v okně **vlastnosti** , když vyberete uzel, který představuje model v **Průzkumníkovi služby BDC**. Ve výchozím nastavení je název modelu **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Změna názvů identifikátorů entit v modelu
 Pokud po nasazení modelu změníte název identifikátoru, může se zobrazit chyba nasazení. Tuto chybu nelze vyřešit nastavením vlastnosti **přírůstkové aktualizace** modelu na **hodnotu NEPRAVDA**. Tento model musíte odvolat ručně a pak znovu nasadit řešení. Další informace najdete v tématu [řešení potíží s řešeními služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). Této chybě se můžete vyhnout nastavením vlastnosti **přírůstkové aktualizace** na **hodnotu NEPRAVDA** , než začnete model nasazovat.

## <a name="locate-documentation-for-bdc-model-elements"></a>Vyhledat dokumentaci pro prvky modelu služby BDC
 Visual Studio přidá prvek XML do modelu pro každou entitu, metodu nebo jinou položku, kterou vytvoříte. Atributy elementu se zobrazí jako vlastnosti v okně **vlastnosti** . Informace o prvcích a atributech, které Visual Studio generuje při návrhu modelu, najdete v tématu [BDCMetadata Schema](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)|Popisuje nástroje, které můžete použít k vizuálnímu návrhu modelu služby BDC.|
|[Postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)|Ukazuje, jak přidat do modelu externí typy obsahu neboli entity.|
|[Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)|Ukazuje, jak přidat metodu, která uživatelům umožňuje zobrazit seznam entit v seznamu nebo ve webové části.|
|[Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)|Ukazuje, jak přidat metodu, která uživatelům umožňuje zobrazit podrobnosti konkrétní entity.|
|[Postupy: Přidání metody autora](../sharepoint/how-to-add-a-creator-method.md)|Ukazuje, jak přidat metodu, která umožňuje uživatelům přidávat záznamy do zdroje dat přímo ze seznamu nebo z webové části.|
|[Postupy: Přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)|Ukazuje, jak přidat metodu, která umožňuje uživatelům odebrat data ze zdroje dat pomocí možností v uživatelském rozhraní (UI) seznamu nebo webové části.|
|[Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)|Ukazuje, jak přidat metodu, která umožňuje uživatelům změnit záznamy dat ve zdroji dat přímo ze seznamu nebo z webové části.|
|[Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Ukazuje, jak použít okno podrobností metody v aplikaci Visual Studio k přidání vstupních a návratových parametrů do metody.|
|[Postupy: definování deskriptoru typu pro parametr](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Ukazuje, jak definovat datové typy parametrů v modelu.|
|[Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)|Ukazuje, jak vytvořit instanci metody, kterou se BDC spouští.|
|[Postupy: Přidání deskriptoru filtru do vyhledávací metody](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Ukazuje, jak uživatelům povolit omezení počtu instancí vrácených vyhledávací metodou.|
|[Vytváření přidružení mezi entitami](../sharepoint/creating-an-association-between-entities.md)|Popisuje, jak můžete definovat vztahy mezi entitami v modelu. Obchodní data Webové části, externí seznamy a vlastní aplikace mohou tyto datové vztahy zobrazit v uživatelském rozhraní (UI).|
|[Postupy: vytvoření přidružení mezi entitami](../sharepoint/how-to-create-an-association-between-entities.md)|Ukazuje, jak definovat vztahy mezi entitami v modelu.|
|[Návod: Createan externí seznam ve službě SharePoint s použitím obchodních dat](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Obsahuje podrobné pokyny, které ukazují, jak vytvořit a otestovat model, který zobrazuje kontakty v externím seznamu služby SharePoint.|
|[Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|V této části najdete Přehled vytváření a navrhování modelů služby BDC.|
