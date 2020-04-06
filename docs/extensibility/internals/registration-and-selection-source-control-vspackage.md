---
title: Registrace a výběr (správa zdrojového kódu VSPackage) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705724"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrace a výběr (balíček VSPackage správy zdrojového kódu)
Zdrojovládací prvek VSPackage musí být registrovány vystavit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]na . Pokud je registrováno více než jeden zdrojový ovládací prvek VSPackage, uživatel může vybrat, který VSPackage načíst ve vhodných časech. Viz [VSPackages](../../extensibility/internals/vspackages.md) další podrobnosti o VSPackages a jak je zaregistrovat.

## <a name="registering-a-source-control-package"></a>Registrace balíčku správy zdrojového kódu
 Balíček správy zdrojového kódu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je registrován tak, aby ho prostředí mohlo najít a dotazovat se na jeho podporované funkce. To je v souladu s schéma zpoždění načítání, ve kterém je vytvořena instance balíčku pouze v případě, že jeho funkce nebo příkazy jsou požadovány nebo jsou požadovány explicitně.

 VSPackages umístit informace v klíči registru specifické pro verzi,\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y*, kde *X* je hlavní číslo verze a *Y* je číslo dílčí verze. Tento postup poskytuje možnost podporovat souběžnou instalaci více verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aplikace .

 Uživatelské [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní (UI) podporuje výběr z více nainstalovaných modulů plug-in správy zdrojového kódu (prostřednictvím balíčku adaptéru zdrojového kódu) a také zdrojové správy VSPackages. Současně může existovat pouze jeden aktivní modul plug-in správy zdrojového kódu nebo vspackage. Však jak je popsáno níže, IDE umožňuje přepínání mezi moduly plug-in správy zdrojového kódu a VSPackages prostřednictvím mechanismu automatického řešení založené na balíček prohození. Existují některé požadavky na straně správy zdrojového kódu VSPackage povolit tento mechanismus výběru.

### <a name="registry-entries"></a>Položky registru
 Balíček správy zdrojového kódu potřebuje tři soukromé identifikátory GUID:

- Guid balíčku: Toto je hlavní identifikátor GUID pro balíček, který obsahuje implementaci správy zdrojového kódu (nazývanou ID_Package v této části).

- Identifikátor GUID správy zdrojového kódu: Toto je identifikátor GUID pro ovládací prvek zdrojového kódu VSPackage, který slouží k registraci se zakázaným inzerováním zdrojového kódu sady Visual Studio a používá se také jako identifikátor GUID kontextu uživatelského rozhraní příkazu. Identifikátor GUID služby správy zdrojového kódu je registrován pod identifikátorem GUID správy zdrojového kódu. V příkladu se identifikátor GUID správy zdrojového kódu nazývá ID_SccProvider.

- Identifikátor GUID služby správy zdrojového kódu: Jedná se o identifikátor GUID soukromé služby používaný v sadě Visual Studio (v této části se nazývá SID_SccPkgService). Kromě toho balíček správy zdrojového kódu musí definovat další identifikátory GUID pro položky VSPackages, okna nástrojů a tak dále.

  Následující položky registru musí být provedeny zdrojového ovládacího prvku VSPackage:

| Název klíče | Položky |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (výchozí) = rg_sz:{ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (výchozí) =\<rg_sz: Popisný název> balíčku<br /><br /> Služba = rg_sz:{SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (výchozí) = rg_sz:#\<ID prostředku pro lokalizované názvové><br /><br /> Balíček = rg_sz:{ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Všimněte si, `SourceCodeControl`že název klíče, , je již používán [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a není k dispozici jako volba pro \<PackageName>.) | (výchozí) = rg_sz:{ID_Package} |

## <a name="selecting-a-source-control-package"></a>Výběr balíčku správy zdrojového kódu
 Několik modulů plug-in modulů plug-in založených na rozhraní API a správy zdrojového kódu VSPackages může být registrována současně. Proces výběru modulu plug-in správy zdrojového kódu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nebo VSPackage musí zajistit, že zatížení plug-in nebo VSPackage ve vhodnou dobu a může odložit načítání nepotřebné součásti, dokud nejsou požadovány. Kromě toho [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musí odebrat veškeré ui z jiných neaktivních VSPackages, včetně položek nabídky, dialogových oken a panelů nástrojů a zobrazit ui pro aktivní VSPackage.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]načte zdrojový ovládací prvek VSPackage, pokud je provedena některá z následujících operací:

- Řešení je otevřeno (pokud je řešení pod shodou zdrojového kódu).

   Při otevření řešení nebo projektu pod správou zdrojového kódu ide způsobí, že ovládací prvek zdroj VSPackage, který byl určen pro toto řešení, které mají být načteny.

- Všechny příkazy nabídky správy zdrojového kódu VSPackage jsou provedeny.

  Zdroj ovládacího prvku VSPackage by měl načíst všechny součásti, které potřebuje pouze v případě, že jsou skutečně bude použit (jinak označované jako zpožděné načítání).

### <a name="automatic-solution-based-vspackage-swapping"></a>Automatické proměňování v balíčcích založených na řešení
 Ovládací prvek zdrojového kódu VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] můžete ručně zaměnit pomocí dialogového okna **Možnosti** v kategorii **Správa zdrojového kódu.** Automatické prohození balíčku založené na řešení znamená, že balíček správy zdrojového kódu, který byl určen pro konkrétní řešení, je při otevření tohoto řešení automaticky nastaven na aktivní. Každý balíček správy <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>zdrojového kódu by měl implementovat a . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zpracovává přepínač mezi moduly plug-in správy zdrojového kódu (implementace rozhraní API modulu plug-in správy zdrojového kódu) a ovládacím prvkem zdrojového kódu VSPackages.

 Balíček adaptéru správy zdrojového kódu se používá k přepnutí na libovolný modul plug-in modulového modulu modulu nastavení rozhraní API správy zdrojového kódu. Proces přepnutí na zprostředkující balíček adaptéru správy zdrojového kódu a určení, který modul plug-in správy zdrojového kódu musí být nastaven na aktivní nebo neaktivní, je pro uživatele transparentní. Balíček adaptéru je vždy aktivní, pokud je aktivní libovolný modul plug-in správy zdrojového kódu. Přepínání mezi dvěma moduly plug-in správy zdrojového kódu znamená pouhé načtení a uvolnění dll plug-in. Přepnutí do správy zdrojového kódu VSPackage však zahrnuje interakci s ide načíst příslušné VSPackage.

 Zdrojový prvek VSPackage je volána při otevření libovolného řešení a klíč registru pro VSPackage je v souboru řešení. Při otevření řešení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] najde hodnotu registru a načte příslušný zdrojový prvek VSPackage. Všechny zdrojové správy VSPackages musí mít položky registru popsané výše. Řešení, které je pod spouštění zdrojového kódu je označenjako přidružené k určité správy zdrojového kódu VSPackage. Zdroj ovládacího prvku VSPackages musí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> implementovat povolit automatické řešení založené na prohození vbalíček.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio UI pro výběr a přepínání balíčků
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Poskytuje uI pro správě zdrojového kódu VSPackage a plug-in výběr v dialogovém okně **Možnosti** v kategorii **Správa zdrojového kódu.** Umožňuje uživateli vybrat aktivní modul plug-in pro řízení zdrojového kódu nebo balíček VSPackage. Rozevírací seznam obsahuje:

- Všechny nainstalované balíčky správy zdrojového kódu

- Všechny nainstalované moduly plug-in správy zdrojového kódu

- Možnost "none", která zakáže správě zdrojového kódu

  Je viditelné pouze uI pro aktivní volbu správy zdrojového kódu. Výběr VSPackage skryje uI pro předchozí VSPackage a zobrazí uI pro nový. Aktivní VSPackage je vybrán na základě pro jednotlivé uživatele. Pokud má uživatel více [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kopií otevřít současně, každý z nich může potenciálně použít jiný aktivní VSPackage. Pokud je ke stejnému počítači přihlášeno více uživatelů, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] může mít každý uživatel samostatné instance otevřené, každý s jiným aktivním balíčkem VSPackage. Pokud více instancí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jsou uzavřeny uživatelem, zdrojový prvek VSPackage, který byl aktivní pro poslední otevřené řešení se stane výchozí zdrojový prvek VSPackage, které mají být nastaveny aktivní při restartování.

  Na rozdíl od [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]předchozích verzí aplikace IDE restartování již není jediným způsobem, jak přepnout řízení zdrojového kódu VSPackages. Výběr vbalíčku je automatický. Přepínání balíčků vyžaduje uživatelská oprávnění systému Windows (nikoli správce nebo power user).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Funkce](../../extensibility/internals/source-control-vspackage-features.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
