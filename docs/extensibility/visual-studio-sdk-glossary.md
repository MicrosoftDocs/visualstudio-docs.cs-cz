---
title: Glosář sady Visual Studio SDK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1de93e49e6d29616868e42a3017cb1737c3bf307
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922884"
---
# <a name="visual-studio-sdk-glossary"></a>Visual Studio SDK Glosář
Tento glosář obsahuje definice podmínek, které se používají v [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dokumentaci.  
  
## <a name="terms"></a>Podmínky  
 doplněk  
 Nástroj pro aplikace, ovladač nebo jiný software přidané do primární aplikace. V sadě Visual Studio integrované vývojové prostředí (IDE) je doplněk aplikace založené na službě Automation, která rozšiřuje možnosti integrovaného vývojového prostředí.  
  
 model automatizace  
 Model automatizace, známá v předchozích verzích sady Visual Studio jako model rozšiřitelnosti, je programovací rozhraní, které poskytuje přístup k základní rutiny tuto jednotku integrovaného vývojového prostředí. Doplňky, průvodci a makra použít objekty v modelu automatizace pro ovládací prvek nebo rozšiřovat funkce integrovaného vývojového prostředí.  
  
 příkaz kontextu uživatelského rozhraní  
 Identifikátor GUID přidružení, zda se příkaz uživatelského rozhraní nebo element jako je panel nástrojů. Příkaz kontextu uživatelského rozhraní je na rozdíl od kontext výběru není připojen k časového období.  
  
 Příkaz kontextu uživatelského rozhraní umožňuje:  
  
- Identifikátor GUID přiřadíte panel nástrojů, který se zobrazí, když se aktivuje konkrétní okno.  
  
- Přiřadíte identifikátor GUID na dostupnost příkazu bez nutnosti načtení nebo spuštění VSPackage.  
  
- Přiřaďte GUID ovlivnit aktivní vazbu klíče.  
  
- Přiřadíte identifikátor GUID zapnout záznam makra.  
  
- Přiřadíte identifikátor GUID k aktivaci režimu ladění nebo přepínat mezi návrhem a režimu běhu v editoru.  
  
  komponenta  
  Část software, který můžete vytvořit součást funkce aplikace bez této aplikace má již existující informace o implementaci pro software. Komunikace mezi komponenty a aplikace je výhradně prostřednictvím rozhraní OLE style.  
  
  Správce komponent  
  Služby `SOleComponentManager`, který poskytuje služby koordinace bez uživatelského rozhraní pro součásti nejvyšší úrovně. `SOleComponentManager` Služba implementuje `IOleComponentManager` rozhraní.  
  
  Správce součástí uživatelského rozhraní  
  Služby `SOleComponentUIManager`, který poskytuje uživatelské rozhraní koordinace služby. `SOleComponentUIManager` Služba implementuje `IOleComponentUIManager` a `IOleInPlaceComponentUIManager` rozhraní.  
  
  místní kontejner objektů a dat  
  `IVsUserContext` Objekt (objekt modelu COM) připojené k jako součást prostředí. Tento objekt obsahuje klíčová slova pro vyhledávání, **F1** klíčová slova a atributy, které se vztahují na komponentu. Kontext kontejnery objektů a dat dále odkazovat na žádné kontext kontejnery objektů a dat, které jsou propojeny k nim.  
  
  Poskytovatel kontextu  
  Komponenta v integrovaném vývojovém prostředí, který se má kontext kontejneru s ním spojená. Tyto součásti zahrnují panel nástrojů, editor nebo projekt hierarchie.  
  
  návrhář  
  Programovací rozhraní, který umožňuje uživatelům pracovat s prvky uživatelského rozhraní (formuláře, tlačítka a další ovládací prvky).  
  
  DocData  
  Objekt modelu COM zapouzdření podkladová data dokumentu ve světě, ve kterých je oddělení dokument/zobrazení (například v případě text editor, by to byl textové vyrovnávací paměti základního všechna zobrazení textového editoru). Pokud EditorFactory neposkytuje tento objekt, rozhraní IDE vyrábí jeden svým jménem. Odpovědnosti tento objekt je ke správě trvalost dat a sdílení sémantiky pro více zobrazení přes to stejné `DocData`. Pokud `DocData` podporuje `IOleCommandTarget` rozhraní, je zahrnutý v směrování příkazů UIShell.  
  
  DocObject.  
  Technologie používaná k hostování uživatelského rozhraní v rámci poskytovány tímto hostitelem. Přesněji řečeno, tento výraz odkazuje na všechny vložení, který podporuje `IOleDocument` a souvisejících rozhraní. Tato technologie má mnoho možných aplikací, jako jsou podrobnosti implementace modelu COM dokumentů, oken nástrojů v jazyce Visual Basic 5.0, návrháři ActiveX v jazyce Visual Basic 6.0 a tak dále.  
  
  dokument  
  Používá k odkazování na dokument jako celek obecně – jak `DocData` a `DocView`. Například DocumentFrame obsahuje `DocView`, ale také uchovává odkaz na `DocData` zpracování trvalosti.  
  
  DocView  
  DocObject, vložení/WindowPane, pomocí kterého uživatel pracuje na Zobrazit a pracovat s podkladovým `DocData`. Není uživatelé využívají výhod Document/View oddělení, který je součástí `DocObject` návrh rozhraní. Uživatelé používat celý DocObject tak, aby fungoval jako zobrazení namísto použití více abstraktní (a méně formalizovanou) pojem podkladová data označované jako `DocData`. `DocView` objekty jsou vždy integrované s objekty rámce dokumentu (podřízených oken MDI) rozhraní IDE.  
  
  DTE  
  `DTE` (Rozšíření nástrojů pro vývoj) objektu je úplně nahoře přístupový bod v modelu automatizace sady Visual Studio, který umožňuje programově automatizovat a rozšířit rozhraní IDE.  
  
  Okna dynamické nápovědy  
  Okno nástroje, které je implementované integrovaným vývojovým prostředím a zobrazí seznam vyhledávání – klíčové slovo nebo **F1** témata nápovědy.  
  
  editor  
  Kód (třída, identifikátor CLSID), který implementuje `DocView`. Implementuje navíc `DocData` Pokud podporuje zobrazení a data oddělení.  
  
  přípona  
  Funkce, která upravuje, upraví nebo přidá do rozhraní IDE. Vytváření rozšíření pomocí modelu automatizace nebo rozšíření VSPackages.  
  
  externí editor  
  Editor, který se neomezuje jen na rozhraní IDE, jako je například Microsoft Word. Byl zaregistrován prostřednictvím vlastní mechanismy a je možné mimo rozhraní IDE. Pokud tento editor může být vložen, zobrazí se v rámci okna v rozhraní IDE. Pokud nemůže být vložený, se vytvoří samostatné okno nejvyšší úrovně.  
  
  hierarchie  
  Strom uzlů, každý uzel přidružený sadu vlastností.  
  
  součást nezávislé nejvyšší úrovně  
  Komponenta, která používá nemodálního okna nejvyšší úrovně a může efektivně pracovat jako samostatné aplikace rozhraní okna, ale je implementována jako objekt v rámci procesu. Proto musí komponentu nezávislé nejvyšší úrovně koordinovat modalitě a služba smyčky zpráv pomocí integrovaného vývojového prostředí. Objekty v rámci procesu nemají své vlastní smyčku zpráv.  
  
  Poskytovatel informací o  
  Informace o zprostředkovatel je modul, který můžete vyhledat klíčová slova a vrátí seznam témat, formu `IVsUserContextItem` objekty. K poskytování **F1** – klíčové slovo vyhledávání položek pro zprostředkovatele informace, zaregistrujte zkompilovaný soubor nápovědy (*. HxS*) se systémem. Témata nápovědy v těchto souborech zadejte seznam témat týkajících se zobrazí v okně Dynamická nápověda a zobrazí, zda uživatel stiskne **F1**.  
  
  místní komponenty  
  Objekt VSPackage, která implementuje `IOleInPlaceComponent` rozhraní pro správu okno, které je vizuálně obsažené v okně dokumentu vlastněné integrovaného vývojového prostředí. Místní součásti není součástí standardní OLE-slučování nabídek; Místo toho jsou jejich prvky uživatelského rozhraní integrace do integrovaného vývojového prostředí.  
  
  Existují dva typy místní komponenty: standardní kabelové místní komponenty a ovládací prvky komponenty.  
  
  Standardní kabelové místní součásti mají nabídky, panely nástrojů a příkazů, které jsou úzce integrovány do uživatelského rozhraní IDE, jako povolí, pokud byly vytvořeny přímo do integrovaného vývojového prostředí.  
  
  Součásti ovládacích prvků nemáte žádný vlastní prvky uživatelského rozhraní, integrovaný do rozhraní IDE; Místo toho používají nabídek rozhraní IDE, příkazy a panelů nástrojů. Může například použít příkaz tučné mají být zobrazena tučně vybrané aplikace word v rámci ovládacího prvku RTF vložené ve formuláři. Součásti ovládacích prvků však může vyžádat, aby dynamicky nainstalované komponenty konkrétní prvky uživatelského rozhraní zobrazily.  
  
  Služba jazyka  
  Sada objektů, které umožňuje vývojářům VSPackage k implementaci funkcí editory kódu jazyka počítače, jako je text označení a barevné označování.  
  
  Různé soubory projektu  
  Projekt používá k uložení otevřených souborů, které nejsou v každém projektu. Seznam položek v tomto projektu není trvalý.  
  
  projekt  
  Projekty jsou tvořené hierarchie objekty nebo objekty COM, které implementují `IVsHierarchy` rozhraní.  
  
  specifické pro projekt návrháři nebo editoru  
  Návrhář, který nelze použít bez ohledu na jejich typ projektu. Všechny návrháře specifické pro projekt, musíte zadat informace o jejich objekt pro vytváření editoru v registru. Integrované vývojové prostředí pak můžete vytvořit instanci Návrháře pokaždé, když určitý typ souboru se otevře v konkrétním projektu.  
  
  okno projektu – typ  
  Okno, které neustále sleduje hierarchie aktuálně aktivní projektu a položek z kontextu globálního výběru. Pomocí typu projektu windows `SVsTrackSelectionEx` IDE změny výstrah a zobrazit zpětné vazby pro uživatele. Průzkumník řešení je příkladem okno typ projektu.  
  
  Vlastnosti – okno  
  Dříve prohlížeč vlastností.  
  
  Projekty založené na odkaz  
  Projekt, který nevyžaduje, aby soubory projektu ve stejném adresáři. Místo toho odkazy na soubory z jiných adresářů nesouvisejících ukládání a udržuje samotného projektu.  
  
  spuštění tabulky dokumentů  
  Vnitřní strukturu, pomocí kterého rozhraní IDE udržuje seznam všech aktuálně otevřených dokumentů. Seznam obsahuje všechny otevřené dokumenty v paměti bez ohledu na to, zda dokumenty jsou právě upravována. Dokument je všechny položky, které se uloží, včetně uložených procedur otevřít v editoru, soubory v projektu nebo souboru hlavního projektu (například soubor *.vcproj).  
  
  Kontext výběru  
  Data, která je součástí podrobností každého okna v rozhraní IDE a slouží ke sledování aktivních výběrů. Výběr kontext se skládá z:  
  
- Ukazatel `IVsHierarchy` rozhraní hierarchie projektu  
  
- Identifikátor položky, položky projektu.  
  
- Ukazatel `ISelectionContainer` rozhraní poskytuje přístup k vlastnostem pro aktivní objekty.  
  
- Pole hodnoty prvku.  
  
  service  
  Kontrakt pro sadu rozhraní modelu COM, který se nachází v jednom objektu COM. Při vytváření služby, který je určený identifikátorem GUID, můžete definovat sadu rozhraní modelu COM, které provádí služba. Objekty modelu COM pomocí služby pro komunikaci mezi sebou.  
  
  Řešení  
  Skupina souvisejících projektů, se kterými uživatel pracuje.  
  
  Standardní návrháře  
  Návrhář, který je možné nezávisle na typu projektu. Všechny standardní návrháře musíte zadat informace o jejich objekt pro vytváření editoru v registru. Integrované vývojové prostředí pak můžete vytvořit instanci Návrháře při každém otevření souboru s konkrétní příponou. Data musíte zachovat do souboru.  
  
  Standardní editor  
  Editor, který je možné nezávisle na žádné konkrétní typ projektu. Takové editory obsahují EditorFactories zaregistrovaný v registru. To umožňuje rozhraní IDE k vyhledání a vyvolání editoru.  
  
  Standardní editor operačního systému  
  Visual Studio konkrétní obsažení, který není. Je zaregistrované pomocí dobře známých klíčů Win32 (například Průzkumník systému Win32 ví, jak vyvolat). Pokud takové editor může být vložen, editor stále hlásí na příslušné místo v integrovaném vývojovém prostředí. V opačném případě se vytvoří samostatné okno nejvyšší úrovně pro takové editory.  
  
  kontext kontejner objektů a dat  
  `IVsUserContext` Objekt propojený s kontejner kontextu. Objekt obsahuje klíčová slova pro vyhledávání, **F1** klíčová slova a atributy pro výběr v rámci jako součást integrované vývojové prostředí. Kontext příklady příkazu v panelu nástrojů nebo klíčové slovo v editoru.  
  
  Seznam úkolů  
  Panel nástrojů, které je implementované integrovaným vývojovým prostředím a zobrazí seznam aktivních úloh.  
  
  Vyrovnávací paměť textu  
  Běžný název pro objekt `VSTextBuffer`.  
  
  Zobrazení textu  
  Běžný název pro objekt `VSTextView`.  
  
  součást nejvyšší úrovně nástroje  
  Komponenta, která funguje jako nemodálního automaticky otevíraném okně, úzce koordinaci s uživatelským rozhraním rozhraní IDE. Stejně jako nezávislé komponenty nejvyšší úrovně musí komponenty nejvyšší úrovně nástroje také koordinovat modalitě a služba smyčky zpráv pomocí integrovaného vývojového prostředí.  
  
  součást nejvyšší úrovně  
  VSPackage objekt, který spravuje nemodální okno nejvyšší úrovně namísto klientské oblasti okna IDE. Nejvyšší úrovně komponenty implementovaly `IOleComponent` rozhraní, abyste mohli využívat služba smyčky zpráv, jako je například přístup do nečinnosti.  
  
  Aktivní uživatelského rozhraní  
  Objekt balíčku VSPackage, který je viditelný a má právě fokus.  
  
  Hierarchie uživatelského rozhraní  
  Objekt modelu COM, který implementuje `IVsUIHierarchy` rozhraní umožňuje zobrazení hierarchie. V okně hierarchie uživatelského rozhraní implementuje `ISelectionContainer` rozhraní aktualizovat v okně Vlastnosti; ostatní okna typ projektu můžete tuto implementaci použít v případě potřeby.  
  
  VSCT  
  Tabulky příkazů sady Visual Studio. Souboru .vsct obsahuje informace o umístění a chování, nabídek, panelů nástrojů a příkazů ve formátu XML.  
  
  VSPackage  
  Instalovatelné softwarového produktu, který přispívá jeden nebo více z následujících položek je rozšířením rozhraní IDE sady Visual Studio: uživatelské rozhraní, služby, typy projektů nebo editoru nebo návrháře. VSPackage se skládá z objektu modelu COM, který implementuje `IVsPackage` rozhraní a jeden nebo více jiných objektů COM, které implementují jiných rozhraní pro podporu výběru a další funkce. Kromě toho VSPackage má požadavky na konkrétní registraci.