---
title: Glosář sady Visual Studio SDK | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 332e606e689e9394f2fcdc8cbc902e2d4a6e5ab5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698159"
---
# <a name="visual-studio-sdk-glossary"></a>Glosář sady Visual Studio SDK
Tento glosář obsahuje definice termínů, [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] které se používají v dokumentaci.

## <a name="terms"></a>Výrazy
 Doplněk Nástrojová aplikace, ovladač nebo jiný software přidaný do primární aplikace. V integrovaném vývojovém prostředí sady Visual Studio (IDE) je doplněk aplikace založená na automatizaci, která rozšiřuje možnosti integrovaného prostředí.

 Model automatizace Model automatizace, známý v předchozích verzích sady Visual Studio jako model rozšiřitelnosti, je programovací rozhraní, které umožňuje přístup k základním rutinám, které řídí rozhraní IDE. Doplňky, průvodci a makra používají objekty v modelu automatizace k řízení nebo rozšíření funkcí rozhraní IDE.

 příkaz Kontext uživatelského rozhraní Přidružení identifikátoru GUID s viditelností příkazu uživatelského rozhraní nebo prvku, například panelu nástrojů. Kontext ui příkazu je na rozdíl od kontextu výběru v tom, že není připojen k oknu.

 Kontext příkazového ui lze použít k:

- Přiřaďte identifikátor GUID k panelu nástrojů, který se zobrazí při aktivaci určitého okna.

- Přiřaďte identifikátor GUID k dostupnosti příkazu bez nutnosti načíst nebo spustit balíček VSPackage.

- Přiřaďte identifikátor GUID, který ovlivní vazbu aktivního klíče.

- Přiřaďte identifikátor GUID k zapnutí záznamu makra.

- Přiřaďte identifikátor GUID k aktivaci režimu ladění nebo k přepínání mezi režimem návrhu a spuštění v editoru.

  component Část softwaru, která může být součástí funkce aplikace, aniž by tato aplikace měla všechny již existující informace o implementaci softwaru. Komunikace mezi komponentou a aplikací probíhá výhradně prostřednictvím rozhraní stylu OLE.

  Správce komponent Služba `SOleComponentManager`, která poskytuje služby koordinace neuživatelského rozhraní pro součásti nejvyšší úrovně. Služba `SOleComponentManager` implementuje `IOleComponentManager` rozhraní.

  správce uživatelského rozhraní `SOleComponentUIManager`komponenty A služba , která poskytuje služby koordinace uživatelského rozhraní. Služba `SOleComponentUIManager` implementuje `IOleComponentUIManager` `IOleInPlaceComponentUIManager` rozhraní a.

  kontextová `IVsUserContext` taška Objekt (objekt COM) připojený ke součásti prostředí. Tento objekt obsahuje vyhledávací klíčová slova, klíčová slova **F1** a atributy, které se vztahují k komponentě. Kontexttašky navíc přejděte na všechny podkontextové tašky, které jsou s nimi propojeny.

  zprostředkovatel kontextu Součást v ide, která má kontextový vak s ním spojené. Tyto součásti zahrnují okno nástroje, editor nebo hierarchii projektu.

  Návrhář Programovací rozhraní, které umožňuje uživatelům manipulovat s prvky uživatelského rozhraní (formuláře, tlačítka a další ovládací prvky).

  DocData Objekt COM zapouzdřující podkladová data dokumentu ve světě, kde je oddělení dokumentu/zobrazení (například v případě textového editoru by to byla textová vyrovnávací paměť, která je základem všech zobrazení textového editoru). Pokud EditorFactory neposkytuje tento objekt, ide vyrábí jeden jeho jménem. Odpovědnost tohoto objektu je spravovat trvalost dat a sdílení sémantiku pro více zobrazení přes totéž `DocData`. Pokud `DocData` objekt podporuje `IOleCommandTarget` rozhraní, je součástí směrování příkazů prostředí UIShell.

  DocObject Technologie slouží k hostování uI v rámci poskytované hostitelem. Přesněji řečeno, tento termín odkazuje na `IOleDocument` jakékoli vkládání, které podporuje a související rozhraní. Tato technologie má mnoho potenciálních aplikací, jako jsou podrobnosti implementace dokumentů COM, okna nástrojů v jazyce Visual Basic 5.0, návrháři ActiveX v jazyce Visual Basic 6.0 a tak dále.

  dokument: Slouží k obecnému odkazu na dokument `DocData` jako `DocView`celek – jak na . Například DocumentFrame obsahuje `DocView`, ale také zachová odkaz `DocData` na pro zpracování trvalost.

  DocView DocObject/Embedding/WindowPane, se kterým uživatel spolupracuje k zobrazení `DocData`a manipulaci s podkladem . Uživatelé nevyužívají výhod oddělení document/view, které `DocObject` je součástí návrhu rozhraní. Uživatelé používají celý DocObject fungovat jako zobrazení namísto použití více abstraktní (a méně `DocData`formalizované) pojem podkladových dat známý jako . `DocView`objekty jsou vždy vloženy s objekty rámečku dokumentu (podřízenými okny MDI) integrovaného prostředí.

  DTE `DTE` Objekt (Rozšiřitelnost vývojových nástrojů) je nejvíce nejnavštěvovanějším přístupovým bodem v modelu automatizace sady Visual Studio, který umožňuje programově automatizovat a rozšířit rozhraní IDE.

  Okno nástroje dynamické nápovědy, které je implementováno nástrojem IDE a zobrazuje seznam vyhledávacího klíčového slova nebo témat nápovědy **F1.**

  editor kód (třída, CLSID), `DocView`který implementuje . Také implementuje, `DocData` pokud je podporováno zobrazení a oddělení dat.

  rozšíření Funkce, která upravuje, přizpůsobuje nebo přidává do rozhraní IDE. Rozšíření můžete vytvořit pomocí modelu automatizace nebo VSPackages.

  externí editor Editor, který není specifický pro rozhraní IDE, například Microsoft Word. Byla registrována prostřednictvím vlastních mechanismů a může být použita mimo ide. Pokud tento editor lze vložit, zobrazí se v okně v integrovaném rozhraní. Pokud jej nelze vložit, vytvoří se samostatné okno nejvyšší úrovně.

  hierarchie Strom uzlů, každý uzel přidružený k sadě vlastností.

  nezávislá komponenta nejvyšší úrovně Komponenta, která používá nemodivé okno nejvyšší úrovně a může efektivně fungovat jako samostatné okno aplikace, ale je implementována jako objekt v procesu. Proto musí nezávislá komponenta nejvyšší úrovně koordinovat modalitu a služby smyčky zpráv s ide. Objekty v procesu nemají vlastní smyčku zpráv.

  poskytovatel informací Poskytovatel informací je modul, který dokáže vyhledat klíčová slova a `IVsUserContextItem` vrátit seznam témat ve formě objektů. Chcete-li poskytnout položky klíčových slov **F1** a vyhledávání pro poskytovatele informací, zaregistrujte zkompilovaný soubor nápovědy (*. HxS*) se systémem. Témata nápovědy v těchto souborech poskytují seznam témat zobrazených v okně Dynamické nápovědy a zobrazení, zda uživatel stiskne **klávesu F1**.

  na místě komponenty VSPackage objekt, `IOleInPlaceComponent` který implementuje rozhraní pro správu okna, které je vizuálně obsaženo v okně dokumentu vlastněné ide. Místní součásti se neúčastní standardního slučování nabídek OLE; místo toho integrují své prvky uživatelského rozhraní do rozhraní IDE.

  Existují dva typy součástí na místě: pevně zapojené komponenty a ovládací prvky komponent.

  Pevně integrované komponenty mají nabídky, panely nástrojů a příkazy, které jsou pevně integrovány do uživatelského rozhraní integrovaného prostředí IDE a vypadají, jako by byly integrovány přímo do integrovaného vývojového prostředí.

  Ovládací prvky komponent nemají žádné vlastní prvky uživatelského rozhraní integrované do integrovaného vývojového prostředí; místo toho používají nabídky, příkazy a panely nástrojů prostředí IDE. Příkaz Tučné lze například použít k tučnému vybranému slovu v ovládacím prvku s formátovaným textem vloženém do formuláře. Ovládací prvky komponent však můžete požadovat, aby dynamicky instalované prvky uživatelského rozhraní specifické pro komponenty.

  Jazyková služba Sada objektů, která vývojářům aplikace VSPackage umožňuje implementovat funkce editorů kódu počítačového jazyka, jako je označování textu a vybarvení.

  Různé soubory projektu Project slouží k domu otevřené soubory, které nejsou v žádném projektu. Seznam položek v tomto projektu není trvalý.

  projekt projekt projekt projekty jsou tvořeny objekty hierarchie nebo COM objekty, které implementují `IVsHierarchy` rozhraní.

  Návrhář nebo editor specifický pro projekt Návrhář, který nelze použít nezávisle na typu projektu. Všichni návrháři specifické pro projekt musí zadat informace editor factory v registru. IDE pak můžete vytvořit instanci návrháře při každém otevření určitého typu souboru v určitém projektu.

  Okno typu projektu Okno, které neustále sleduje aktuálně aktivní hierarchii projektu a položku z kontextu globálního výběru. Okna typu project `SVsTrackSelectionEx` používají službu k upozornění ide změn a zobrazení zpětné vazby pro uživatele. Průzkumník řešení je příkladem okna typu projektu.

  Okno Vlastnosti Dříve prohlížeč vlastností.

  projekty založené na odkazech Projekt, který nevyžaduje soubory pro projekt, který má být ve stejném adresáři. Místo toho jsou odkazy na soubory z jiných nesouvisejících adresářů uloženy a udržovány samotným projektem.

  spuštění tabulky dokumentů Vnitřní struktura, kterou ide udržuje seznam všech aktuálně otevřených dokumentů. Seznam obsahuje všechny otevřené dokumenty v paměti bez ohledu na to, zda jsou dokumenty právě upravovány. Dokument je libovolná položka, která je uložena, včetně uložených procedur otevřených v editoru, souborů v projektu nebo v hlavním souboru projektu (například soubor *.vcproj).

  kontext výběru Data, která jsou součástí podrobností každého okna v ide a slouží ke sledování aktivních výběrů. Kontext výběru se skládá z:

- Ukazatel na `IVsHierarchy` rozhraní hierarchie projektu

- Identifikátor položky projektu.

- Ukazatel na `ISelectionContainer` rozhraní poskytující přístup k vlastnostem aktivních objektů.

- Pole hodnot prvků.

  služba: Smlouva pro sadu rozhraní COM, která je umístěna v jednom objektu COM. Při vytváření služby, která je identifikována identifikátorem GUID, definujete sadu rozhraní COM, která provádí službu. Objekty MODELU COM používají služby ke komunikaci mezi sebou.

  řešení Skupina souvisejících projektů, se kterými uživatel pracuje.

  standardní návrhář Návrhář, který lze použít nezávisle na typu projektu. Všichni standardní návrháři musí zadat informace editorfactory v registru. IDE pak můžete vytvořit instanci návrháře při každém otevření souboru s určitou příponou. Data musí uchovávat do souboru.

  standardní editor editor, který lze použít nezávisle na konkrétním typu projektu. Tito redaktoři mají EditorFactories registrovány v registru. To umožňuje rozhraní IDE vyhledat a vyvolat editor.

  standardní editor operačního systému Vkládání, které není specifické pro Visual Studio. Je registrován pomocí známých win32 klíče (například Win32 Explorer ví, jak vyvolat). Pokud takový editor může být vložen, editor stále zobrazí na svém místě v integrovaném rozhraní. V opačném případě je pro tyto editory vytvořeno samostatné okno nejvyšší úrovně.

  podkontextová `IVsUserContext` taška Objekt spojený s kontextovou taškou. Objekt obsahuje vyhledávací klíčová slova, klíčová slova **F1** a atributy pro výběr v rámci komponenty IDE. Příklady podkontextu zahrnují příkaz v okně nástroje nebo klíčové slovo v editoru.

  Okno nástroje seznamu úkolů, které je implementováno nástrojem IDE a zobrazuje seznam aktivních úkolů.

  textový vyrovnávací paměť Běžný `VSTextBuffer`název objektu .

  Zobrazení textu Běžný název `VSTextView`objektu .

  součást nejvyšší úrovně nástroje Komponenta, která funguje jako nemodivé vyskakovací okno a úzce koordinuje s uživatelským rozhraním rozhraní IDE. Stejně jako nezávislé součásti nejvyšší úrovně musí součásti nejvyšší úrovně nástroje také koordinovat modalitu a služby smyčky zpráv s ide.

  Komponenta nejvyšší úrovně Objekt VSPackage, který spravuje nemodlavé okno nejvyšší úrovně namísto klientské oblasti okna IDE. Součásti nejvyšší úrovně `IOleComponent` implementují rozhraní, aby využily služeb smyčky zpráv, jako je například přístup k době nečinnosti.

  Aktivní objekt UI VSPackage, který je viditelný a aktuálně má fokus.

  Hierarchie uživatelského rozhraní Objekt `IVsUIHierarchy` COM, který implementuje rozhraní, aby bylo možné zobrazit hierarchii. Okno hierarchie uživatelského `ISelectionContainer` rozhraní implementuje rozhraní pro aktualizaci okna Vlastnosti; ostatní okna typu projektu můžete použít tuto implementaci, v případě potřeby.

  VSCT Visual Studio příkaz tabulky. Soubor .vsct obsahuje informace o umístění a chování nabídek, panelů nástrojů a příkazů ve formátu XML.

  VSPackage Instalovatelný software, který rozšiřuje rozhraní IDE sady Visual Studio tím, že přispívá jednou nebo více z následujících položek: uživatelské rozhraní, služby, typy projektů nebo editor/návrhář. VSPackage se skládá z objektu COM, který implementuje `IVsPackage` rozhraní a jeden nebo více dalších objektů COM, které implementují další rozhraní pro podporu výběru a další funkce. Kromě toho VSPackage má specifické požadavky na registraci.
