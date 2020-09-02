---
title: Registrace a výběr (VSPackage správy zdrojového kódu) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705724"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrace a výběr (balíček VSPackage správy zdrojového kódu)
Aby bylo možné zpřístupnit rozhraní VSPackage správy zdrojového kódu, musí být zaregistrováno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Pokud je registrováno více než jeden prvek VSPackage správy zdrojového kódu, může uživatel vybrat, který VSPackage se má načíst v odpovídajících časech. Další informace o VSPackage a o tom, jak je zaregistrovat, najdete v tématu [VSPackage](../../extensibility/internals/vspackages.md) .

## <a name="registering-a-source-control-package"></a>Registrace balíčku správy zdrojového kódu
 Balíček správy zdrojového kódu je zaregistrován, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ho prostředí mohl najít a dotaz na jeho podporované funkce. Je v souladu se schématem pro opožděné načítání, ve kterém se vytvoří instance balíčku pouze v případě, že jsou funkce nebo příkazy požadovány nebo jsou požadovány explicitně.

 Sady VSPackage umístí informace do klíče registru specifického pro verzi HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *X. Y*, kde *X* je číslo hlavní verze a *Y* je číslo vedlejší verze. Tento postup nabízí možnost podporovat souběžnou instalaci více verzí nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Uživatelské rozhraní (UI) podporuje výběr z více instalovaných modulů plug-in pro správu zdrojového kódu (prostřednictvím balíčku pro správu zdrojového kódu) i správy zdrojového kódu. V jednom okamžiku může být pouze jeden modul plug-in nebo VSPackage aktivního ovládacího prvku zdrojového kódu. Jak je popsáno níže, integrované vývojové prostředí (IDE) umožňuje přepínání mezi moduly plug-in správy zdrojového kódu a VSPackage prostřednictvím automatického mechanismu výměny balíčků, který je založený na řešení. Pro povolení tohoto mechanismu výběru existují některé požadavky na součást balíčku VSPackage správy zdrojového kódu.

### <a name="registry-entries"></a>Položky registru
 Balíček správy zdrojového kódu potřebuje tři privátní identifikátory GUID:

- GUID balíčku: Toto je hlavní identifikátor GUID balíčku, který obsahuje implementaci správy zdrojových kódů (s názvem ID_Package v této části).

- Identifikátor GUID správy zdrojového kódu: Jedná se o identifikátor GUID pro VSPackage správy zdrojového kódu, který se používá k registraci ve službě Visual Studio Source Control stub a používá se také jako identifikátor GUID kontextu uživatelského rozhraní příkazu. Identifikátor GUID služby správy zdrojového kódu je zaregistrován pod identifikátorem GUID správy zdrojového kódu. V příkladu se identifikátor GUID správy zdrojového kódu nazývá ID_SccProvider.

- GUID služby správy zdrojového kódu: Jedná se o identifikátor GUID privátní služby, který používá Visual Studio (nazývaný SID_SccPkgService v této části). Kromě toho musí balíček správy zdrojových kódů definovat jiné identifikátory GUID pro VSPackage, okna nástrojů atd.

  Následující položky registru musí být vytvořeny pomocí balíčku VSPackage správy zdrojového kódu:

| Název klíče | Položky |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (výchozí) = rg_sz: {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (výchozí) = rg_sz:\<Friendly name of Package><br /><br /> Služba = rg_sz: {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (výchozí) = rg_sz: #\<Resource ID for localized name><br /><br /> Balíček = rg_sz: {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Všimněte si, že název klíče, `SourceCodeControl` , je již používán nástrojem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a není k dispozici jako volba pro \<PackageName> .) | (výchozí) = rg_sz: {ID_Package} |

## <a name="selecting-a-source-control-package"></a>Výběr balíčku správy zdrojového kódu
 Některé moduly plug-in založené na rozhraní API pro správu zdrojového kódu a rozšíření pro správu zdrojového kódu mohou být souběžně registrovány. Proces výběru modulu plug-in správy zdrojových kódů nebo VSPackage musí zajistit, aby se v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] příslušném čase načetl modul plug-in nebo VSPackage, a může odložit načítání zbytečných součástí, dokud nebudou vyžadovány. Kromě toho [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je nutné odebrat všechna uživatelská rozhraní z jiných neaktivních VSPackage, včetně položek nabídky, dialogových oken a panelů nástrojů, a zobrazit uživatelské rozhraní pro aktivní VSPackage.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Načte VSPackage správy zdrojového kódu, když se provede kterákoli z následujících operací:

- Řešení je otevřeno (když je řešení pod správou zdrojových kódů).

   Když je otevřeno řešení nebo projekt pod správou zdrojového kódu, rozhraní IDE způsobí načtení balíčku pro správu zdrojového kódu, který byl určen pro toto řešení.

- Spustí se všechny příkazy nabídky balíčku VSPackage správy zdrojového kódu.

  VSPackage správy zdrojového kódu by měl načítat jakékoli součásti, které potřebuje, jenom když se skutečně budou používat (jinak označované jako opožděné načítání).

### <a name="automatic-solution-based-vspackage-swapping"></a>Automatické prohození balíčku VSPackage založené na řešení
 Pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dialogového okna **Možnosti** v kategorii **Správa zdrojového kódu** můžete ručně prohodit správu zdrojového kódu. Automatické prohození balíčků založené na řešení znamená, že balíček správy zdrojového kódu, který je určený pro konkrétní řešení, je automaticky nastaven na aktivní, když je toto řešení otevřeno. Každý balíček správy zdrojového kódu by měl implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zpracovává přepínač mezi moduly plug-in správy zdrojového kódu (implementací rozhraní API modulu plug-in správy zdrojových kódů) a VSPackage správy zdrojového kódu.

 Balíček řídicího adaptéru zdrojového kódu se používá pro přepnutí na libovolný modul plug-in založený na modulu API pro správu zdrojového kódu. Proces přepnutí do balíčku zprostředkujícího adaptéru správy zdrojového kódu a určení, který modul plug-in správy zdrojových kódů musí být nastaven na hodnotu aktivní nebo neaktivní, je pro uživatele transparentní. Pokud je aktivní libovolný modul plug-in správy zdrojových kódů, je balíček adaptéru vždy aktivní. Přepínání mezi dvěma moduly plug-in pro správu zdrojového kódu – stačí k načtení a uvolnění knihovny DLL modulu plug-in. Přepnutí na VSPackage správy zdrojového kódu nicméně zahrnuje interakci s IDE k načtení vhodného VSPackage.

 Rozhraní VSPackage správy zdrojového kódu se volá, když se otevře nějaké řešení a klíč registru pro VSPackage je v souboru řešení. Po otevření řešení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] najde hodnotu registru a nahraje příslušný balíček VSPackage správy zdrojového kódu. Všechny VSPackage správy zdrojového kódu musí obsahovat položky registru popsané výše. Řešení, které je pod správou zdrojových kódů, je označeno jako přidružené ke konkrétnímu balíčku VSPackage správy zdrojového kódu. Sady VSPackage správy zdrojového kódu musí implementovat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> aby povolovaly automatické výměny VSPackage založené na řešení.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Uživatelské rozhraní sady Visual Studio pro výběr a přepínání balíčku
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje uživatelské rozhraní pro VSPackage správy zdrojového kódu a výběr modulů plug-in v dialogovém okně **Možnosti** v kategorii **Správa zdrojového kódu** . Umožňuje uživateli vybrat modul plug-in nebo VSPackage aktivního ovládacího prvku pro správu zdrojového kódu. Rozevírací seznam obsahuje:

- Všechny nainstalované balíčky správy zdrojového kódu

- Všechny nainstalované moduly plug-in správy zdrojových kódů

- Možnost None, která zakazuje řízení zdrojového kódu

  Je viditelné pouze uživatelské rozhraní pro volbu aktivní správy zdrojového kódu. Výběr VSPackage skryje uživatelské rozhraní pro předchozí VSPackage a zobrazí uživatelské rozhraní pro nový. Aktivní VSPackage se vybere na základě jednotlivých uživatelů. Pokud má uživatel více kopií [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] otevřených souběžně, může každý z nich potenciálně použít jiný aktivní VSPackage. Pokud se ke stejnému počítači přihlašuje více uživatelů, může mít každý uživatel samostatné instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Open, z nichž každý má jiný aktivní VSPackage. Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatel zavře víc instancí, sada VSPackage správy zdrojového kódu, která byla aktivní pro poslední otevřené řešení, se stala výchozím ovládacím prvkem VSPackage pro správu zdrojového kódu, která se nastaví jako aktivní při restartu.

  Na rozdíl od předchozích verzí nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] není RESTARTOVÁNÍ IDE již jediným způsobem, jak přepínat VSPackage správy zdrojového kódu. Výběr VSPackage je automatický. Přepínání balíčků vyžaduje oprávnění uživatele systému Windows (nikoli správce nebo Power Users).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Funkce](../../extensibility/internals/source-control-vspackage-features.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)
