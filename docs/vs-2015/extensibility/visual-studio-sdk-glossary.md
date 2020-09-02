---
title: Glosář sady Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c189c4c9e06d224d7cef296a2c39e732cbc29f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538704"
---
# <a name="visual-studio-sdk-glossary"></a>Glosář sady Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento Glosář poskytuje definice termínů používaných v [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] dokumentaci.  
  
## <a name="terms"></a>Terminologie  
 doplněk  
 Do primární aplikace se přidala pomůcka aplikace, ovladač nebo jiný software. V integrovaném vývojovém prostředí (IDE) sady Visual Studio je doplněk aplikace založené na automatizaci, která rozšiřuje možnosti rozhraní IDE.  
  
 model automatizace  
 Model automatizace, známý v předchozích verzích sady Visual Studio jako model rozšiřitelnosti, je programovací rozhraní, které poskytuje přístup k podkladovým rutinám, které řídí rozhraní IDE. Doplňky, průvodci a makra používají objekty v modelu automatizace pro řízení nebo rozšiřování funkcí rozhraní IDE.  
  
 kontext uživatelského rozhraní příkazu  
 Přidružení identifikátoru GUID k viditelnosti příkazu nebo prvku uživatelského rozhraní, jako je například panel nástrojů. Kontext uživatelského rozhraní příkazu je na rozdíl od kontextu výběru v tom, že není připojen k oknu.  
  
 Kontext uživatelského rozhraní příkazu lze použít pro:  
  
- Přiřaďte identifikátor GUID k panelu nástrojů, který se zobrazí při aktivaci konkrétního okna.  
  
- Přiřaďte identifikátor GUID k dostupnosti příkazu bez nutnosti načíst nebo spustit VSPackage.  
  
- Přiřaďte identifikátor GUID, aby se ovlivnila aktivní vazba klíče.  
  
- Pokud chcete zapnout záznam makra, přiřaďte identifikátor GUID.  
  
- Přiřaďte identifikátor GUID pro aktivaci režimu ladění nebo pro přepínání mezi návrhem a režimem spuštění v editoru.  
  
  komponenta  
  Software, který může být součástí funkcí aplikace bez toho, aby tato aplikace měla žádné existující informace o implementaci softwaru. Komunikace mezi komponentou a aplikací je určena výhradně prostřednictvím rozhraní stylu OLE.  
  
  Správce komponent  
  Služba, `SOleComponentManager` která poskytuje služby pro koordinaci nesouvisející s uživatelským rozhraním pro komponenty nejvyšší úrovně. `SOleComponentManager`Služba implementuje `IOleComponentManager` rozhraní.  
  
  Správce uživatelského rozhraní součásti  
  Služba, `SOleComponentUIManager` která poskytuje služby pro koordinaci uživatelského rozhraní. `SOleComponentUIManager`Služba implementuje `IOleComponentUIManager` `IOleInPlaceComponentUIManager` rozhraní a.  
  
  kontejner kontextu  
  `IVsUserContext`Objekt (objekt com) připojený k součásti prostředí. Tento objekt obsahuje klíčová slova pro vyhledávání, klíčová slova F1 a atributy, které se vztahují k komponentě. Kontextové penalty navíc odkazují na jakékoli penalty podkontextu, které jsou s nimi spojeny.  
  
  Zprostředkovatel kontextu  
  Komponenta v integrovaném vývojovém prostředí, která má přidruženu kontextový kontejner. Mezi tyto komponenty patří okno nástroje, Editor nebo hierarchie projektu.  
  
  návrhář  
  Programovací rozhraní, které umožňuje uživatelům manipulovat s prvky uživatelského rozhraní (formuláře, tlačítka a další ovládací prvky).  
  
  DocData  
  Objekt modelu COM, který zapouzdřuje podkladová data dokumentu v celém světě, kde se nachází oddělení dokumentu/zobrazení (například v případě, že v textovém editoru se jedná o textovou vyrovnávací paměť, která je základem všech zobrazení textového editoru). Pokud objektem EditorFactory tento objekt nedodá, IDE ho bude vyrábět za jeho jménem. Zodpovědností tohoto objektu je spravovat Trvalost dat a sémantiku sdílení pro více zobrazení přes tuto stejnou `DocData` . Pokud `DocData` objekt `IOleCommandTarget` rozhraní podporuje, bude zahrnut do směrování příkazu UIShell.  
  
  DocObject  
  Technologie používaná k hostování uživatelského rozhraní v rámci rámce poskytnutého hostitelem. Konkrétně tento pojem označuje jakékoli vkládání, které podporuje `IOleDocument` rozhraní a související rozhraní. Tato technologie má mnoho potenciálních aplikací, jako jsou například podrobnosti implementace dokumentů modelu COM, okna nástrojů v Visual Basic 5,0, návrháři ActiveX v Visual Basic 6,0 atd.  
  
  dokument  
  Slouží k obecnému odkazování na dokument jako celek – `DocData` a `DocView` . Například DocumentFrame obsahuje `DocView` , ale také uchovává odkaz na, aby se zachovala `DocData` trvalá manipulace.  
  
  Objekt DocView  
  DocObject/vkládání/WindowPane, se kterými se uživatel chová, aby zobrazil a manipuluje s podkladem `DocData` . Všimněte si, že uživatelé nevyužívají oddělení dokumentu/zobrazení, které je součástí `DocObject` návrhu rozhraní. Uživatelé používají celý DocObject jako zobrazení namísto použití více abstraktních (a méně formálních) slov podkladových dat, která se označují jako `DocData` . `DocView` objekty jsou vždy vloženy s objekty rámce dokumentu (podřízená okna MDI) rozhraní IDE.  
  
  DTE  
  `DTE`Objekt (rozšiřitelnost vývojových nástrojů) je nejvyšší přístupový bod v modelu automatizace sady Visual Studio, který umožňuje programově automatizovat a roztáhnout rozhraní IDE.  
  
  Dynamické okno Help  
  Panel nástrojů, který je implementován rozhraním IDE a zobrazuje seznam klíčových slov pro vyhledávání nebo témata nápovědy pro klávesu F1.  
  
  editor  
  Kód (třída, CLSID), který implementuje `DocView` . Také implementuje, `DocData` zda je podporováno zobrazení/oddělení dat.  
  
  přípona  
  Funkce, která upravuje, upravuje nebo přidává rozhraní IDE. Pomocí modelu automatizace nebo VSPackage vytvoříte rozšíření.  
  
  externí editor  
  Editor, který není specifický pro integrované vývojové prostředí (IDE), jako je například Microsoft Word. Byl zaregistrován prostřednictvím vlastních mechanismů a lze jej použít vně rozhraní IDE. Pokud tento editor může být vložen, zobrazí se v rámci okna v integrovaném vývojovém prostředí. Pokud se nedá vložit, vytvoří se samostatné okno nejvyšší úrovně.  
  
  hierarchie  
  Strom uzlů, každý uzel přidružený k sadě vlastností.  
  
  nezávislá součást nejvyšší úrovně  
  Komponenta, která používá nemodální okno nejvyšší úrovně a může pracovat efektivně jako samostatné okno aplikace, ale je implementována jako objekt v procesu. Nezávislá komponenta nejvyšší úrovně musí proto koordinovat rozhraní IDE a služby smyčky zpráv. Vnitroprocesové objekty nemají svou vlastní smyčku zpráv.  
  
  poskytovatel informací  
  Poskytovatel informací je modul, který může vyhledat klíčová slova a vracet seznam témat ve formě `IVsUserContextItem` objektů. Chcete-li zadat položky klíčového slova F1 a vyhledat pro poskytovatele informací, zaregistrujte zkompilovaný soubor s nápovědu (. HxS) se systémem. Témata nápovědy v těchto souborech slouží k poskytnutí seznamu témat zobrazených v dynamickém okně nápovědy a k zobrazení, zda uživatel stiskne klávesu F1.  
  
  místní součást  
  Objekt VSPackage, který implementuje `IOleInPlaceComponent` rozhraní pro správu okna, které je vizuálně obsaženo v okně dokumentu, které vlastní IDE. Místní součásti se neúčastní v nabídce Standard OLE – sloučení; místo toho integrují prvky uživatelského rozhraní do integrovaného vývojového prostředí (IDE).  
  
  Existují dva typy místních součástí: Hardwired místní součásti a ovládací prvky komponent.  
  
  Hardwired místní komponenty obsahují nabídky, panely nástrojů a příkazy, které jsou integrovány těsně do uživatelského rozhraní rozhraní IDE, které se zobrazí, jako kdyby byly sestaveny přímo do rozhraní IDE.  
  
  Ovládací prvky komponenty nemají žádné vlastní prvky uživatelského rozhraní integrované do rozhraní IDE; místo toho používají nabídky, příkazy a panely IDE. Například lze použít tučný příkaz pro tučné písmo vybraného slova v ovládacím prvku formátovaného textu vloženého do formuláře. Ovládací prvky komponent však mohou požádat o zobrazení dynamicky instalovaných prvků uživatelského rozhraní specifických pro komponentu.  
  
  Služba jazyka  
  Sada objektů, která vývojářům VSPackage umožňuje implementovat funkce editorů kódu počítačových jazyků, jako je například textové označení a Colorizing.  
  
  Projekt různých souborů  
  Projekt, který slouží k ustájení otevřených souborů, které nejsou v žádném projektu. Seznam položek v tomto projektu není trvalý.  
  
  projekt  
  Projekty se skládají z objektů hierarchie nebo objektů COM, které implementují `IVsHierarchy` rozhraní.  
  
  Návrhář nebo editor konkrétního projektu  
  Návrhář, který nelze použít nezávisle na typu projektu. Všechny návrháře specifické pro projekt musí v registru zadat své informace o továrně editoru. Rozhraní IDE pak může vytvořit instance návrháře pokaždé, když se v určitém projektu otevře určitý typ souboru.  
  
  okno typu projektu  
  Okno, které nepřetržitě sleduje aktuálně aktivní hierarchii projektu a položku z kontextu globálního výběru. Typ projektu – systém Windows používá `SVsTrackSelectionEx` službu k upozornění na integrované vývojové prostředí (IDE) a k zobrazení zpětné vazby uživateli. Průzkumník řešení je příkladem okna typu projekt.  
  
  Vlastnosti – okno  
  Dřív prohlížeč vlastností.  
  
  projekty založené na odkazech  
  Projekt, který nevyžaduje, aby soubory projektu byly ve stejném adresáři. Místo toho jsou odkazy na soubory z jiných nesouvisejících adresářů uloženy a udržovány samotným projektem.  
  
  běžící tabulka dokumentů  
  Interní struktura, podle které IDE udržuje seznam všech aktuálně otevřených dokumentů. Tento seznam obsahuje všechny otevřené dokumenty v paměti bez ohledu na to, zda jsou dokumenty právě upravovány. Dokument je libovolná položka, která je uložena, včetně uložených procedur, které jsou otevřeny v editoru, souborů v projektu nebo v hlavním souboru projektu (například soubor *. vcproj).  
  
  kontext výběru  
  Data, která jsou součástí podrobností každého okna v integrovaném vývojovém prostředí (IDE) a slouží ke sledování aktivních výběrů. Kontext výběru se skládá z těchto:  
  
- Ukazatel na `IVsHierarchy` rozhraní hierarchie projektu  
  
- Identifikátor položky projektu  
  
- Ukazatel na `ISelectionContainer` rozhraní poskytující přístup k vlastnostem pro aktivní objekty.  
  
- Pole hodnot prvků.  
  
  service  
  Kontrakt pro sadu rozhraní COM, která je umístěna v jednom objektu COM. Když vytváříte službu, která je identifikována identifikátorem GUID, definujete sadu rozhraní COM, která provádí službu. Objekty modelu COM používají služby ke komunikaci mezi sebou.  
  
  řešení  
  Skupina souvisejících projektů, se kterými uživatel pracuje.  
  
  Návrhář úrovně Standard  
  Návrhář, který lze použít nezávisle na typu projektu. Všechny standardní návrháře musí do registru zadat informace o továrně editoru. Rozhraní IDE pak může vytvořit instanci návrháře pokaždé, když je otevřen soubor s určitým rozšířením. Data musí být uchována v souboru.  
  
  standardní editor  
  Editor, který lze použít nezávisle na konkrétním typu projektu. Tyto editory mají v registru zaregistrované EditorFactories. Rozhraní IDE umožňuje najít a vyvolat Editor.  
  
  standardní editor operačního systému  
  Vložení, které není specifické pro Visual Studio. Je zaregistrován pomocí dobře známých klíčů Win32 (například aplikace Win32 Explorer ví, jak vyvolat). Pokud takový editor lze vložit, bude editor stále zobrazen na místě v integrovaném vývojovém prostředí (IDE). V opačném případě se pro tyto editory vytvoří samostatné okno nejvyšší úrovně.  
  
  penalta podkontextu  
  `IVsUserContext`Objekt propojený k balíčku kontextu. Tento objekt obsahuje klíčová slova pro vyhledávání, klíčová slova F1 a atributy pro výběr v rámci komponenty IDE. Příklady podkontextu zahrnují příkaz v okně nástroje nebo klíčové slovo v editoru.  
  
  Seznam úkolů  
  Okno nástroje, které je implementováno pomocí rozhraní IDE a zobrazuje seznam aktivních úloh.  
  
  vyrovnávací paměť textu  
  Běžný název objektu `VSTextBuffer` .  
  
  Textové zobrazení  
  Běžný název objektu `VSTextView` .  
  
  součást nejvyšší úrovně nástroje  
  Komponenta, která funguje jako nemodální místní okno, koordinuje těsně s uživatelským rozhraním IDE. Podobně jako nezávislé komponenty nejvyšší úrovně musí komponenty nejvyšší úrovně nástroje také koordinovat rozhraní IDE a služby smyčky zpráv.  
  
  součást nejvyšší úrovně  
  Objekt VSPackage, který spravuje nemodální okno nejvyšší úrovně místo klientské oblasti okna IDE. Komponenty nejvyšší úrovně implementují `IOleComponent` rozhraní, které umožňuje využívat služby smyčky zpráv, jako je například přístup k času nečinnosti.  
  
  Uživatelské rozhraní aktivní  
  Objekt VSPackage, který je viditelný a aktuálně má fokus.  
  
  Hierarchie uživatelského rozhraní  
  Objekt modelu COM, který implementuje `IVsUIHierarchy` rozhraní, aby bylo možné zobrazit hierarchii. Okno hierarchie uživatelského rozhraní implementuje `ISelectionContainer` rozhraní pro aktualizaci okno Vlastnosti; jiná okna typu projektu mohou tuto implementaci použít, pokud je to žádoucí.  
  
  VSCT  
  Tabulka příkazů sady Visual Studio. Soubor. vsct obsahuje informace o umístění a chování nabídek, panelů nástrojů a příkazů ve formátu XML.  
  
  VSPackage  
  Instalovatelný softwarový software, který rozšiřuje integrované vývojové prostředí sady Visual Studio tím, že přispívá k jednomu nebo více následujícím akcím: uživatelské rozhraní, služby, typy projektů nebo editor/Návrhář. VSPackage se skládá z objektu COM, který implementuje `IVsPackage` rozhraní a jednoho nebo více objektů modelu COM, které implementují jiná rozhraní pro podporu výběru a dalších funkcí. Kromě toho má VSPackage konkrétní požadavky na registraci.
