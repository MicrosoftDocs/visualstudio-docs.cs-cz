---
title: Navrhování modelu připojení obchodních dat | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 27b83cefdaa24e5a439352318aa149ec4e24d09d
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327239"
---
# <a name="design-a-business-data-connectivity-model"></a>Navrhování modelu připojení obchodních dat
  Přidáním entity a metody pro soubor modelu můžete vyvinout model pro službu Business Data Connectivity (BDC). Entity popisuje kolekci datová pole. Například entita může představovat tabulky v databázi. Metoda provede úlohu například přidání, odstranění nebo aktualizace dat reprezentována entity. Další informace najdete v tématu [integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="add-entities"></a>Přidání entity
 Entitu můžete přidat přetažením nebo kopírování **Entity** ze sady Visual Studio **sada nástrojů** do BDC návrháře. Další informace najdete v tématu [postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Definování polí entity v třídě. Například může přidat pole s názvem `Address` k `Customer` třídy. Můžete buď přidejte novou třídu do projektu, nebo použijte existující třídy vytvořené pomocí jiných nástrojů, například Návrhář relací objektů (Návrhář relací objektů). Název entity a název třídy, která reprezentuje entitu nemusí odpovídat. Třída v entitě týkají metody definujete v modelu.  
  
## <a name="add-methods"></a>Přidejte metody
 Když uživatelé zobrazit, přidat, aktualizovat nebo odstranit informace v seznamu nebo webovou část, která je založená na modelu služby BDC volá metody v modelu. Metoda je nutné přidat do modelu pro každý úkol, který může uživatel provádět. Vytvoření metody výběrem jakýkoli z pěti typů základní metoda z **podrobnosti o metodě BDC** okno. Následující tabulka popisuje pět základní metody modelu služby BDC.  
  
|Metoda|Popis|  
|------------|-----------------|  
|Metoda Finder|Vrátí kolekci instancí entit. Voláno, když uživatel otevře seznamu nebo webové části. Další informace najdete v tématu [postupy: přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md).|  
|specifická metoda Finder|Vrátí instanci konkrétní entity. Voláno, když uživatel zobrazí podrobnosti o konkrétní položku v seznamu. Další informace najdete v tématu [postupy: Přidání specifické vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|tvůrce|Přidává nová data do zdroje dat entity. Volá se, když uživatelé vybrat, **novou položku** na pásu karet seznamu, která je založená na modelu. Další informace najdete v tématu [postupy: přidání metody vytvoření](../sharepoint/how-to-add-a-creator-method.md).|  
|aktualizační metoda|Upravuje data v seznamu. Voláno, když uživatelé aktualizovat informace v seznamu. Další informace najdete v tématu [postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md).|  
|metoda odstranění|Odstraní data. Voláno, když uživatelé odstranit položku ze seznamu. Další informace najdete v tématu [postupy: přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## <a name="define-method-parameters"></a>Zadejte parametry metody
 Když vytvoříte metodu, Visual Studio přidá vstupní a výstupní parametry, které jsou vhodné pro typ metody. Tyto parametry jsou jenom zástupné symboly. Ve většině případů je třeba upravit parametry tak, aby předat nebo vrátit správný typ data. Ve výchozím nastavení, například vyhledávací metody vrací řetězec. Ve většině případů budete chtít změnit návratový parametr vyhledávací metody tak, že vrátí kolekci entit. Můžete provést tuto akci změnou popisovač typu parametru. Popisovač typu je kolekce atributů, které popisuje datový typ parametru. Další informace najdete v tématu [postupy: definování deskriptoru typu pro parametr](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Visual Studio umožňuje kopírování popisovače typu mezi parametry v modelu. Například můžete třeba definovat popisovač typu s názvem `CustomerTD` pro návratový parametr `GetCustomer` metoda. Můžete zkopírovat `CustomerTD` zadejte popisovač **Průzkumník modelu BDC**a potom vložte tento popisovač typu pro vstupní parametr `CreateCustomer` metoda. Předchází se tak nutnosti stejné popisovač typu zadat více než jednou.  
  
## <a name="method-instances"></a>Instance metody
 Když vytvoříte metodu, Visual Studio přidá výchozí metoda instance. Instance metody je odkaz na metodu, plus výchozí hodnoty pro parametry. Jediná metoda může mít více instancí metoda. Každá instance je kombinací podpis metody a sadu výchozích hodnot. Další informace najdete v tématu [postupy: definování deskriptoru typu pro parametr](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Když spouštíte projekt, zobrazit instance metoda v rozevíracím seznamu výše seznamu služby SharePoint. Uživatelé mohou metoda instance, které chcete zobrazit data.  
  
 Chcete-li přidat výchozí hodnoty do instance metody, budete muset přímo upravit soubor XML modelu. Další informace najdete v tématu [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## <a name="add-filter-descriptors"></a>Přidat deskriptory filtrů
 Načtení instancí entity, které odpovídají kritériím některé příjemci modelu může být vhodné. Chcete-li tuto funkci povolit, můžete přidat deskriptoru filtru na metodu. Deskriptory filtrů povolení příjemcům modelu pro filtrování sady výsledků metoda předáním hodnoty do metod před jejich provedení. Další informace najdete v tématu [postupy: Přidání parametrů filtru na operace pro omezení instancí z externího systému](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint poskytuje několik funkcí, které umožňují uživatelům poskytovat hodnoty filtru. Například zadejte obchodní Data webové části textového pole filtru. Uživatele můžete omezit data v seznamu tak, že zadáte hodnotu v textovém poli. Další informace o tom, jak přidat deskriptoru filtru do metody najdete v tématu [postupy: Přidání deskriptoru filtru do vyhledávací metody](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### <a name="filter-descriptor-properties"></a>Filtr popisovač vlastnosti
 Musíte nastavit hodnotu **přidružené popisovač typu**, **název**, a **typ** vlastnosti deskriptoru filtru. Všechny ostatní vlastnosti jsou volitelné.  
  
 **Přidružené popisovač typu** vlastnost deskriptoru filtru se vztahem k vstupní parametr. Když uživatel poskytuje hodnota filtru, služby BDC předá tuto hodnotu do metody pomocí vstupní parametr.  
  
 **Typ** vlastnost popisuje filtrování vzor, který chcete použít. Ve službě SharePoint ovlivňuje filtrování vzor, který vyberete text, který se zobrazí v uživatelské rozhraní (uživatelského rozhraní). Například pro filtrování vzor Komparátor, text **rovná** se zobrazí jako ovládací prvek nahoře obchodní Data webové části. Další informace o jednotlivých filtrování vzor najdete v tématu [typy filtrů podporované aplikací BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Další informace o vlastnostech deskriptoru filtru najdete v tématu [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### <a name="provide-default-values"></a>Zadejte výchozí hodnoty
 V některých případech nemusí uživatel zadat hodnotu filtru. Výchozí hodnota můžete poskytovat přidáním výchozí hodnotu do instance metody nebo nastavením výchozí hodnota v kódu metodu. Další informace o tom, jak přidat výchozí hodnotu do instance metody najdete v tématu [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Příklad toho, jak nastavit výchozí hodnotu vstupního parametru v kódu metodu, naleznete v části [postupy: Přidání deskriptoru filtru do vyhledávací metody](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## <a name="validate-the-model"></a>Ověření modelu
 Váš model můžete ověřit během vývoje. Visual Studio identifikuje problémy, které mohou bránit váš model z chovají podle očekávání. Tyto problémy se zobrazují v sadě Visual Studio **seznam chyb**.  
  
 Model můžete ověřit pomocí otevření místní nabídky pro návrháře BDC a pak vyberete **ověřením**. Pokud model obsahuje všechny chyby, se zobrazí v **seznam chyb**. Můžete rychle přesunout kurzor na kód, který obsahuje chybu poklepáním na chybu v seznamu. Jako alternativu můžete zvolit **F8** nebo **Shift**+**F8** klíči opakovaně na krok vpřed nebo zpět prostřednictvím chyby v seznamu.  
  
 Chyby ověření může dojít, když je nějakým způsobem porušena pravidla modelu. Například pokud **IsCollection** typ popisovače je nastavena na **true**, ale neexistuje žádné popisovače podřízeného typu, zobrazí se chyba ověření. Možná budete muset zohlednit pravidla modelu služby BDC pochopit některé chyby, které se zobrazují v sadě Visual Studio **seznam chyb**. Další informace o pravidlech modelu služby BDC najdete v tématu [BDCMetadata schématu](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="debug-the-solution-that-contains-the-model"></a>Ladění řešení, která obsahuje model
 Můžete ladit kód, jako by ladění žádný kód v sadě Visual Studio. Ladění kódu, kdekoli nastavte zarážky v kódu a pak spusťte ladicího programu. Visual Studio otevře web služby SharePoint. Ve službě SharePoint vytvořte na seznam nebo webovou část, která používá obchodní data. Poté můžete procházet váš kód. Další informace o ladění projektů služby SharePoint, naleznete v části [řešení řešení služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 Můžete také ladění kódu v vlastní sestavení, které přidáte do projektu. K ladění kódu v vlastního sestavení, ale musíte přidat sestavení do balíčku řešení. Další informace najdete v tématu [postupy: Přidání a odebrání dalších sestavení](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Další informace o přidání vlastního sestavení do projektu najdete v tématu [postupy: zahrnutí vlastního sestavení ve funkci BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### <a name="configure-bdc-security"></a>Konfigurace zabezpečení BDC
 Možná budete muset změnit nastavení zabezpečení ve službě SharePoint, než můžete ladit, vaše řešení. Chcete-li toto nastavení změnit, otevřete aplikaci Služba Připojení obchodních dat v web služby SharePoint 2010 centrální správy. V **nastavit oprávnění úložiště Metadata** dialogové okno, přidání uživatelského účtu a pak vyberte některé z následujících možností:  
  
|Úloha|Možnost|  
|----------|------------|  
|K nasazení modelů služby BDC.|Upravit|  
|K vytvoření seznamy a webové části pomocí externí typy obsahu (entit) v modelu.|Lze vybrat v klientech|  
|Pokud chcete vytvořit, číst, aktualizovat a odstranit entity data.|Spuštění|  
  
 Další informace o těchto nastaveních najdete v tématu [správy Služba Připojení obchodních dat](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 Můžete také nastavit oprávnění zabezpečení pro jednotlivé modely nebo externích typů obsahu. Další informace o tom, jak nastavit oprávnění zabezpečení modelu najdete v tématu [správu modelu služby BDC](http://go.microsoft.com/fwlink/?LinkID=178884). Další informace o tom, jak nastavit oprávnění zabezpečení externí typu obsahu najdete v tématu [externí obsah správu](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Tato nastavení použijte k ladění řešení na místním serveru SharePoint. Další informace o tom, jak konfigurovat nastavení související s BDC zabezpečení na provozním serveru SharePoint, naleznete v části [Přehled zabezpečení služby Připojení obchodních dat](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### <a name="retract-models-that-become-corrupt"></a>Odvolat modely, které jsou poškozené
 Při prvním spuštění ladicího programu, Visual Studio nasadí celý model do služby SharePoint. Visual Studio pokaždé, když po tomto datu, aktualizuje všechny změny provedené mezi nasazení modelu ve službě SharePoint.  
  
 Můžou nastat situace, kam chcete Visual Studio úplně odvolání modelu ze služby SharePoint. Model, například mohou být poškozené.  Pokud chcete znovu zavést modelu do služby SharePoint, nastavte **přírůstkové aktualizace** vlastnost modelu, který má **False**, a pak spusťte ladicího programu. **Přírůstkové aktualizace** vlastnost se zobrazí v **vlastnosti** okno při výběru uzlu, který představuje model **Průzkumník modelu BDC**. Ve výchozím nastavení, název modelu je **BdcModel1**.  
  
### <a name="change-identifier-names-of-entities-in-the-model"></a>Změňte identifikátor názvy entit v modelu
 Pokud změníte název identifikátoru po nasazení modelu, může se zobrazit chyba nasazení. Tuto chybu nelze vyřešit nastavením **přírůstkové aktualizace** vlastnost modelu, který má **False**. Musíte ručně odvolat modelu a znovu nasaďte řešení. Další informace najdete v tématu [řešení řešení služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). Tato chyba se můžete vyhnout nastavením **přírůstkové aktualizace** vlastnost **False** před nasazením původně modelu.  
  
## <a name="locate-documentation-for-bdc-model-elements"></a>Vyhledejte dokumentace pro prvky modelu služby BDC
 Visual Studio přidá XML element modelu pro každou entitu, metoda nebo jinou položku, kterou vytvoříte. Atributy elementu se zobrazí jako vlastnosti **vlastnosti** okno. Informace o elementy a atributy, které sada Visual Studio generuje při návrhu modelu najdete v tématu [BDCMetadata schématu](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="related-topics"></a>Související témata
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled nástrojů pro navrhování modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)|Popisuje nástroje, které můžete použít pro vizuální návrh model pro Záložní.|  
|[Postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)|Ukazuje, jak přidat externích typů obsahu nebo entity do modelu.|  
|[Postupy: přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)|Ukazuje, jak přidat metodu, která umožňuje uživatelům zobrazení seznamu entit v seznamu nebo webové části.|  
|[Postupy: Přidání specifické vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)|Ukazuje, jak přidat metodu, která umožňuje uživatelům zobrazit podrobnosti o konkrétní entity.|  
|[Postupy: přidání metody vytvoření](../sharepoint/how-to-add-a-creator-method.md)|Ukazuje, jak přidat metodu, která umožňuje uživatelům přidat záznamy na zdroji dat přímo ze seznamu nebo webové části.|  
|[Postupy: přidání metody odstranění](../sharepoint/how-to-add-a-deleter-method.md)|Ukazuje, jak přidat metodu, která umožňuje uživatelům odebrat data ze zdroje dat pomocí možností v uživatelské rozhraní (UI) seznam nebo webové části.|  
|[Postupy: Přidání aktualizační metody](../sharepoint/how-to-add-an-updater-method.md)|Ukazuje, jak přidat metodu, která umožňuje uživatelům měnit záznamy dat ve zdroji dat přímo ze seznamu nebo webové části.|  
|[Postupy: Přidání parametru k metodě](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Ukazuje, jak používat okno podrobností metoda v sadě Visual Studio k přidání parametrů vstupní a zpět na metodu.|  
|[Postupy: definování deskriptoru typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Ukazuje, jak definovat parametr datové typy v modelu.|  
|[Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)|Ukazuje, jak vytvořit instanci metodu, která provede BDC.|  
|[Postupy: Přidání deskriptoru filtru do vyhledávací metody](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Ukazuje, jak povolit uživatelům omezení počtu instancí vrácených funkcí vyhledávací metody.|  
|[Vytváření přidružení mezi entitami](../sharepoint/creating-an-association-between-entities.md)|Popisuje, jak je možné definovat vztahy mezi entit v modelu. Obchodní Data webové části, externí uvádí a vlastních aplikací můžete zobrazit tyto relace mezi daty v uživatelském rozhraní (UI).|  
|[Postupy: vytvoření přidružení mezi entitami](../sharepoint/how-to-create-an-association-between-entities.md)|Ukazuje, jak definovat vztahy mezi entit v modelu.|  
|[Návod: Createan externího seznamu ve službě SharePoint s použitím obchodních dat](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Poskytuje podrobné pokyny, které ukazují, jak vytvořit a otestovat model, který se zobrazí v seznamu SharePoint externí kontakty.|  
|[Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Poskytuje přehled o vytváření a navrhování modelů služby BDC.|  
  
