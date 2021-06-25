---
title: Glosář sady VISUAL STUDIO SDK | Microsoft Docs
description: Tento glosář obsahuje definice termínů, které se používají v dokumentaci Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 49e91a64220882eea196819a1860052dc871bec4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905420"
---
# <a name="visual-studio-sdk-glossary"></a>Glosář sady Visual Studio SDK
Tento glosář obsahuje definice termínů, které se používají v [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dokumentaci.

## <a name="terms"></a>Terminologie
 doplněk: Aplikace nástroje, ovladač nebo jiný software přidaný do primární aplikace. V Visual Studio integrované vývojové prostředí (IDE) je doplněk aplikace založená na automatizaci, která rozšiřuje možnosti integrovaného vývojového prostředí(IDE).

 model automatizace Model automatizace, známý v předchozích verzích Visual Studio jako model rozšiřitelnosti, je programovací rozhraní, které poskytuje přístup k podkladovým rutinám, které řídí integrované vývojové prostředí (IDE). Doplňky, průvodci a makra používají objekty v modelu automatizace k řízení nebo rozšíření funkcí integrovaného vývojového prostředí.

 Přidružení identifikátoru GUID k viditelnosti příkazu nebo elementu uživatelského rozhraní, jako je panel nástrojů, pomocí kontextu uživatelského rozhraní. Kontext uživatelského rozhraní příkazů se liší od kontextu výběru v tom, že není připojený k oknu.

 Kontext uživatelského rozhraní příkazů lze použít k:

- Přiřaďte identifikátor GUID k panelu nástrojů, který se zobrazí při aktivaci konkrétního okna.

- Přiřaďte identifikátor GUID k dostupnosti příkazu, aniž byste museli načíst nebo spustit balíček VSPackage.

- Přiřaďte identifikátor GUID, který ovlivní aktivní vazbu klíče.

- Přiřazením identifikátoru GUID zapnete záznam makra.

- Přiřaďte identifikátor GUID pro aktivaci režimu ladění nebo přepínání mezi návrhem a režimem spuštění v editoru.

  součást softwaru, která může být součástí funkcí aplikace, aniž by tato aplikace měla žádné předchozí informace o implementaci softwaru. Komunikace mezi komponentou a aplikací je výhradně prostřednictvím rozhraní ve stylu OLE.

  component manager (správce komponent) Služba , která poskytuje služby koordinace bez uživatelského rozhraní `SOleComponentManager` pro komponenty nejvyšší úrovně. Služba `SOleComponentManager` implementuje `IOleComponentManager` rozhraní .

  component UI manager (správce uživatelského rozhraní komponent) Služba `SOleComponentUIManager` , která poskytuje služby koordinace uživatelského rozhraní. Služba `SOleComponentUIManager` implementuje rozhraní a `IOleComponentUIManager` `IOleInPlaceComponentUIManager` .

  context bag `IVsUserContext` Objekt (objekt COM) připojený ke komponentě prostředí. Tento objekt obsahuje klíčová slova vyhledávání, klíčová **slova F1** a atributy, které se vztahují k komponentě. Kontextové obaly navíc odkazují na všechny související sádky s dílčími kontexty.

  context provider (poskytovatel kontextu) Komponenta v integrovaném vývojovém prostředí (IDE), ke které je přidružený kontextový sáček. Mezi tyto součásti patří okno nástroje, editor nebo hierarchie projektu.

  designer Programovací rozhraní, které umožňuje uživatelům manipulovat s prvky uživatelského rozhraní (formuláře, tlačítka a další ovládací prvky).

  DocData Objekt COM zapouzdřující podkladová data dokumentu ve světě, kde existuje oddělení dokumentů a zobrazení (například v případě textového editoru by to byla textová vyrovnávací paměť podkladová pro všechna zobrazení textového editoru). Pokud EditorFactory tento objekt nezadá, integrované vývojové prostředí (IDE) ho za něj vyrábí. Zodpovědností tohoto objektu je spravovat trvalost dat a sémantiku sdílení pro více zobrazení v tomto objektu `DocData` . Pokud objekt podporuje rozhraní , je součástí směrování příkazů `DocData` `IOleCommandTarget` prostředí UIShell.

  Technologie DocObject použitá k hostování uživatelského rozhraní v rámci rámce poskytnutého hostitelem. Přesněji řečeno se tento termín týká všech vkládání, která podporují rozhraní a `IOleDocument` související. Tato technologie má mnoho potenciálních aplikací, například podrobnosti implementace dokumentů COM, okna nástrojů v Visual Basic 5.0, návrháři ActiveX v Visual Basic 6.0 a tak dále.

  document Used to refer generically to the document as a whole– both `DocData` a the `DocView` . Například DokumentFrame obsahuje , ale zachová také odkaz na , aby bylo `DocView` `DocData` možné zpracovat trvalost.

  DocView Objekt DocObject/Embedding/WindowPane, se kterým uživatel pracuje při zobrazení a manipulaci s podkladovým objektem `DocData` . Uživatelé nevyuužívejte oddělení dokumentů a zobrazení, které je součástí `DocObject` návrhu rozhraní. Uživatelé používají celý objekt DocObject, aby místo abstraktního (a méně formalizovaného) pojmu podkladových dat, který se označuje jako , choval jako `DocData` zobrazení. `DocView` Objekty jsou vždy vloženy s objekty rámce dokumentu (podřízenými okny MDI) integrovaného vývojového prostředí.

  DTE Objekt (rozšiřitelnost vývojových nástrojů) je nejvyšší přístupový bod v modelu automatizace Visual Studio, který umožňuje programově automatizovat a rozšířit integrované vývojové `DTE` prostředí (IDE).

  Okno dynamického okna nápovědy, které je implementováno v integrovaném vývojovém prostředí a zobrazuje seznam klíčových slov vyhledávání nebo **témat nápovědy F1.**

  editor Code (třída, CLSID), který implementuje `DocView` . Implementuje se také `DocData` v případě, že je podporováno zobrazení a oddělení dat.

  rozšíření Funkce, která upravuje, přizpůsobuje nebo přidává do integrovaného vývojového prostředí (IDE). Rozšíření vytvoříte pomocí modelu automatizace nebo rozšíření VSPackage.

  external editor (externí editor) Editor, který není specifický pro integrované vývojové prostředí (IDE), například Microsoft Word. Byla zaregistrována prostřednictvím vlastních mechanismů a lze ji použít mimo integrované vývojové prostředí.) Pokud je možné tento editor vložit, zobrazí se v rámci okna v integrovaném vývojovém prostředí. Pokud ho nelze vložit, vytvoří se samostatné okno nejvyšší úrovně.

  hierarchie Strom uzlů, každý uzel přidružený k sadě vlastností.

  nezávislá komponenta nejvyšší úrovně Komponenta, která používá ne moderované okno nejvyšší úrovně a může pracovat efektivně jako samostatné okno aplikace, ale je implementována jako objekt v procesu. Nezávislá komponenta nejvyšší úrovně proto musí koordinovat modality a služby smyčky zpráv s rozhraním IDE. Objekty v procesu nemají vlastní smyčku zpráv.

  poskytovatel informací Poskytovatel informací je modul, který může hledat klíčová slova a vracet seznam témat ve formě `IVsUserContextItem` objektů. Pokud chcete **zprostředkovateli** informací poskytnout F1 a vyhledat položky klíčových slov, zaregistrujte zkompilovaný soubor nápovědy (*. HxS*) se systémem . Témata nápovědy v těchto souborech obsahují seznam témat zobrazených v okně dynamické nápovědy a zobrazují, jestli uživatel stiskne **klávesu F1**.

  místně místně: Objekt VSPackage, který implementuje rozhraní pro správu okna, které je vizuálně obsaženo v okně dokumentu `IOleInPlaceComponent` vlastněného rozhraním IDE. Místní komponenty se neúčastní standardního slučování nabídek OLE. místo toho integrují své prvky uživatelského rozhraní do integrovaného vývojového prostředí (IDE).

  Existují dva typy komponent na místě: pevně zapojené komponenty a ovládací prvky komponent.

  Místní komponenty s pevným kabelem obsahují nabídky, panely nástrojů a příkazy, které jsou těsně integrované do uživatelského rozhraní integrovaného vývojového prostředí ( IDE). Zdá se, že jsou integrované vývojové prostředí přímo integrované.

  Ovládací prvky komponent nemají žádné vlastní prvky uživatelského rozhraní integrované do integrovaného vývojového prostředí. Místo toho používají nabídky, příkazy a panely nástrojů integrovaného vývojového prostředí. Příkaz Bold můžete například použít k tučnému písmu vybraného slova v ovládacím prvku formátovaný text vloženého do formuláře. Ovládací prvky komponent však mohou požadovat zobrazení dynamicky nainstalovaných prvků uživatelského rozhraní specifických pro jednotlivé komponenty.

  služba jazyka Sada objektů, která vývojářům VSPackage umožňuje implementovat funkce editorů počítačového jazyka kódu, jako je označování textu a jejich zabarvení.

  Projekt Různé soubory se používá k tomu, aby bylo možné uchovat otevřené soubory, které nejsou v žádném projektu. Seznam položek v tomto projektu se neuchová.

  Projektové projekty jsou tvořeny objekty hierarchie nebo objekty MODELU COM, které implementují `IVsHierarchy` rozhraní.

  Návrhář nebo editor specifický pro projekt Návrhář, který nelze použít nezávisle na typu projektu. Všichni návrháři pro konkrétní projekt musí v registru zadat své informace o objektech pro vytváření editoru. Integrované vývojové prostředí pak může vytvořit instanci návrháře při každém otevření určitého typu souboru v určitém projektu.

  okno typu projektu Okno, které neustále sleduje aktuálně aktivní hierarchii projektu a položku z globálního kontextu výběru. Okna typu projektu používají službu k upozorní integrovanému vývojovému prostředí (IDE) na změny a zobrazí `SVsTrackSelectionEx` uživateli zpětnou vazbu. Průzkumník řešení je příkladem okna typu projektu.

  okno Vlastnosti dříve Prohlížeč vlastností.

  Projekt projektů založených na odkazech, který nevyžaduje, aby soubory pro projekt byly ve stejném adresáři. Odkazy na soubory z jiných nesouvisejících adresářů se místo toho ukládají a udržují v samotném projektu.

  spuštění tabulky dokumentů Interní struktura, podle které integrované vývojové prostředí udržuje seznam všech aktuálně otevřených dokumentů. Seznam obsahuje všechny otevřené dokumenty v paměti bez ohledu na to, jestli se dokumenty právě upravuje. Dokument je libovolná uložená položka, včetně uložených procedur otevřených v editoru, souborů v projektu nebo hlavního souboru projektu (například souboru *.vcproj).

  kontext výběru Data, která jsou součástí podrobností každého okna v integrovaném vývojovém prostředí a slouží ke sledování aktivních výběrů. Kontext výběru se skládá z těchto lekcí:

- Ukazatel na `IVsHierarchy` rozhraní hierarchie projektu

- Identifikátor položky projektu

- Ukazatel na rozhraní `ISelectionContainer` poskytující přístup k vlastnostem pro aktivní objekty.

- Pole hodnot prvků

  service Kontrakt pro sadu rozhraní modelu COM, která se nachází v jednom objektu COM. Když vytvoříte službu, která je identifikována identifikátorem GUID, definujete sadu rozhraní modelu COM, která službu provádí. Objekty COM používají služby ke komunikaci mezi sebou.

  solution Group of related projects with a user works.

  standardní návrhář Návrhář, který lze použít nezávisle na typu projektu. Všichni standardní návrháři musí v registru zadat své informace o objektech pro vytváření editoru. Integrované vývojové prostředí pak může vytvořit instanci návrháře při každém otevření souboru s konkrétní příponou. Data musí být uložená v souboru.

  Editor standardního editoru, který lze použít nezávisle na libovolném konkrétním typu projektu. Tyto editory mají v registru zaregistrované editory EditorFactories. To umožňuje integrovaného vývojového prostředí vyhledat a vyvolat editor.

  Standardní editor operačního systému Vkládání, které Visual Studio specifické. Je zaregistrován pomocí dobře známých klíčů Win32 (například aplikace Win32 Explorer ví, jak vyvolat). Pokud takový editor může být vložen, Editor se stále zobrazuje na místě v integrovaném vývojovém prostředí (IDE). V opačném případě se pro tyto editory vytvoří samostatné okno nejvyšší úrovně.

  dílčí kontext – `IVsUserContext` objekt propojený do balíčku kontextu. Objekt obsahuje klíčová slova pro vyhledávání, klíčová slova **F1** a atributy pro výběr v rámci komponenty IDE. Příklady podkontextu zahrnují příkaz v okně nástroje nebo klíčové slovo v editoru.

  Okno nástroje seznam úkolů, které je implementováno pomocí rozhraní IDE a zobrazuje seznam aktivních úloh.

  Běžný název textové vyrovnávací paměti pro objekt `VSTextBuffer` .

  Běžný název zobrazení textu pro objekt `VSTextView` .

  komponenta na nejvyšší úrovni nástroje součást, která funguje jako nemodální překryvné okno, koordinuje se těsně s uživatelským rozhraním integrovaného vývojového prostředí (IDE). Podobně jako nezávislé komponenty nejvyšší úrovně musí komponenty nejvyšší úrovně nástroje také koordinovat rozhraní IDE a služby smyčky zpráv.

  komponenta nejvyšší úrovně objekt VSPackage, který spravuje nemodální okno nejvyšší úrovně místo klientské oblasti okna IDE. Komponenty nejvyšší úrovně implementují `IOleComponent` rozhraní, které umožňuje využívat služby smyčky zpráv, jako je například přístup k času nečinnosti.

  Uživatelské rozhraní aktivní objekt VSPackage, který je viditelný a aktuálně má fokus.

  Hierarchie uživatelského rozhraní objekt COM, který implementuje `IVsUIHierarchy` rozhraní, aby bylo možné zobrazit hierarchii. Okno hierarchie uživatelského rozhraní implementuje `ISelectionContainer` rozhraní pro aktualizaci okno Vlastnosti; jiná okna typu projektu mohou tuto implementaci použít, pokud je to žádoucí.

  VSCT příkazová tabulka sady Visual Studio. Soubor. vsct obsahuje informace o umístění a chování nabídek, panelů nástrojů a příkazů ve formátu XML.

  VSPackage instalovatelný softwarový software, který rozšiřuje rozhraní IDE sady Visual Studio tím, že přispívá k jednomu nebo několika z následujících položek: uživatelské rozhraní, služby, typy projektů nebo editor/Návrhář. VSPackage se skládá z objektu COM, který implementuje `IVsPackage` rozhraní a jednoho nebo více objektů modelu COM, které implementují jiná rozhraní pro podporu výběru a dalších funkcí. Kromě toho má VSPackage konkrétní požadavky na registraci.
