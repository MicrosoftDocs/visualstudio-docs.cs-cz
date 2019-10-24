---
title: Registrace a výběr (VSPackage správy zdrojového kódu) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d6ca60c74ae9956f38418ea6048bb0c8050be2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724510"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrace a výběr (balíček VSPackage správy zdrojového kódu)
Aby bylo možné zpřístupnit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], musí být balíček VSPackage správy zdrojového kódu zaregistrován. Pokud je registrováno více než jeden prvek VSPackage správy zdrojového kódu, může uživatel vybrat, který VSPackage se má načíst v odpovídajících časech. Další informace o VSPackage a o tom, jak je zaregistrovat, najdete v tématu [VSPackage](../../extensibility/internals/vspackages.md) .

## <a name="registering-a-source-control-package"></a>Registrace balíčku správy zdrojového kódu
 Balíček správy zdrojového kódu je zaregistrovaný, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí mohl najít a dotaz na jeho podporované funkce. Je v souladu se schématem pro opožděné načítání, ve kterém se vytvoří instance balíčku pouze v případě, že jsou funkce nebo příkazy požadovány nebo jsou požadovány explicitně.

 VSPackage umístí informace do klíče registru specifického pro verzi HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\*X. Y*, kde *X* je hlavní číslo verze a *Y* je číslo menší verze. Tento postup nabízí možnost podporovat souběžnou instalaci více verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Rozhraní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uživatelské rozhraní podporuje výběr z více instalovaných modulů plug-in pro správu zdrojového kódu (prostřednictvím balíčku správy zdrojového kódu) i správy zdrojového kódu. V jednom okamžiku může být pouze jeden modul plug-in nebo VSPackage aktivního ovládacího prvku zdrojového kódu. Jak je popsáno níže, integrované vývojové prostředí (IDE) umožňuje přepínání mezi moduly plug-in správy zdrojového kódu a VSPackage prostřednictvím automatického mechanismu výměny balíčků, který je založený na řešení. Pro povolení tohoto mechanismu výběru existují některé požadavky na součást balíčku VSPackage správy zdrojového kódu.

### <a name="registry-entries"></a>Položky registru
 Balíček správy zdrojového kódu potřebuje tři privátní identifikátory GUID:

- GUID balíčku: Toto je hlavní identifikátor GUID balíčku, který obsahuje implementaci správy zdrojových kódů (s názvem ID_Package v této části).

- Identifikátor GUID správy zdrojového kódu: Jedná se o identifikátor GUID pro VSPackage správy zdrojového kódu, který se používá k registraci ve službě Visual Studio Source Control stub a používá se také jako identifikátor GUID kontextu uživatelského rozhraní příkazu. Identifikátor GUID služby správy zdrojového kódu je zaregistrován pod identifikátorem GUID správy zdrojového kódu. V příkladu se identifikátor GUID správy zdrojového kódu nazývá ID_SccProvider.

- Identifikátor GUID služby správy zdrojového kódu: Toto je privátní GUID služby, kterou používá Visual Studio (s názvem SID_SccPkgService v této části). Kromě toho musí balíček správy zdrojových kódů definovat jiné identifikátory GUID pro VSPackage, okna nástrojů atd.

  Následující položky registru musí být vytvořeny pomocí balíčku VSPackage správy zdrojového kódu:

| Název klíče | Položky |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (výchozí) = RG_SZ: {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (výchozí) = RG_SZ: \<Friendly název balíčku ><br /><br /> Služba = RG_SZ: {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (výchozí) = RG_SZ: # \<Resource ID pro lokalizovaný název ><br /><br /> Package = RG_SZ: {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Všimněte si, že název klíče, `SourceCodeControl`, je již využíván [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a není k dispozici jako volba pro \<PackageName >.) | (výchozí) = RG_SZ: {ID_Package} |

## <a name="selecting-a-source-control-package"></a>Výběr balíčku správy zdrojového kódu
 Některé moduly plug-in založené na rozhraní API pro správu zdrojového kódu a rozšíření pro správu zdrojového kódu mohou být souběžně registrovány. Proces výběru modulu plug-in nebo VSPackage pro správu zdrojového kódu musí zajistit, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načetly modul plug-in nebo VSPackage v příslušném čase, a může odložit načítání zbytečných součástí, dokud nebudou požadovány. Kromě toho musí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odebrat všechna uživatelská rozhraní z jiných neaktivních VSPackage, včetně položek nabídky, dialogových oken a panelů nástrojů, a zobrazit uživatelské rozhraní pro aktivní VSPackage.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načte VSPackage správy zdrojového kódu, když se provede kterákoli z následujících operací:

- Řešení je otevřeno (když je řešení pod správou zdrojových kódů).

   Když je otevřeno řešení nebo projekt pod správou zdrojového kódu, rozhraní IDE způsobí načtení balíčku pro správu zdrojového kódu, který byl určen pro toto řešení.

- Spustí se všechny příkazy nabídky balíčku VSPackage správy zdrojového kódu.

  VSPackage správy zdrojového kódu by měl načítat jakékoli součásti, které potřebuje, jenom když se skutečně budou používat (jinak označované jako opožděné načítání).

### <a name="automatic-solution-based-vspackage-swapping"></a>Automatické prohození balíčku VSPackage založené na řešení
 Pomocí dialogového okna **možnosti** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v kategorii **Správa zdrojového kódu** můžete ručně prohodit správu zdrojového kódu. Automatické prohození balíčků založené na řešení znamená, že balíček správy zdrojového kódu, který je určený pro konkrétní řešení, je automaticky nastaven na aktivní, když je toto řešení otevřeno. Každý balíček správy zdrojového kódu by měl implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zpracovává přepínač mezi moduly plug-in správy zdrojového kódu (implementací rozhraní API modulu plug-in správy zdrojových kódů) a VSPackage správy zdrojového kódu.

 Balíček řídicího adaptéru zdrojového kódu se používá pro přepnutí na libovolný modul plug-in založený na modulu API pro správu zdrojového kódu. Proces přepnutí do balíčku zprostředkujícího adaptéru správy zdrojového kódu a určení, který modul plug-in správy zdrojových kódů musí být nastaven na hodnotu aktivní nebo neaktivní, je pro uživatele transparentní. Pokud je aktivní libovolný modul plug-in správy zdrojových kódů, je balíček adaptéru vždy aktivní. Přepínání mezi dvěma moduly plug-in pro správu zdrojového kódu – stačí k načtení a uvolnění knihovny DLL modulu plug-in. Přepnutí na VSPackage správy zdrojového kódu nicméně zahrnuje interakci s IDE k načtení vhodného VSPackage.

 Rozhraní VSPackage správy zdrojového kódu se volá, když se otevře nějaké řešení a klíč registru pro VSPackage je v souboru řešení. Po otevření řešení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] najde hodnotu registru a načte příslušný balíček VSPackage pro správu zdrojového kódu. Všechny VSPackage správy zdrojového kódu musí obsahovat položky registru popsané výše. Řešení, které je pod správou zdrojových kódů, je označeno jako přidružené ke konkrétnímu balíčku VSPackage správy zdrojového kódu. Sady VSPackage správy zdrojového kódu musí implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>, aby se povolilo automatické prohození sady VSPackage založené na řešení.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Uživatelské rozhraní sady Visual Studio pro výběr a přepínání balíčku
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje uživatelské rozhraní pro VSPackage správy zdrojového kódu a výběr modulů plug-in v dialogovém okně **Možnosti** v kategorii **Správa zdrojového kódu** . Umožňuje uživateli vybrat modul plug-in nebo VSPackage aktivního ovládacího prvku pro správu zdrojového kódu. Rozevírací seznam obsahuje:

- Všechny nainstalované balíčky správy zdrojového kódu

- Všechny nainstalované moduly plug-in správy zdrojových kódů

- Možnost None, která zakazuje řízení zdrojového kódu

  Je viditelné pouze uživatelské rozhraní pro volbu aktivní správy zdrojového kódu. Výběr VSPackage skryje uživatelské rozhraní pro předchozí VSPackage a zobrazí uživatelské rozhraní pro nový. Aktivní VSPackage se vybere na základě jednotlivých uživatelů. Pokud má uživatel více kopií [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] otevřeno souběžně, každá z nich může potenciálně použít jiný aktivní VSPackage. Pokud se ke stejnému počítači přihlašuje více uživatelů, může mít každý uživatel samostatné instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] otevřít, z nichž každý má jiný aktivní VSPackage. Když uživatel zavře víc instancí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], otevře se sada VSPackage správy zdrojového kódu, která byla aktivní pro poslední otevřené řešení, jako výchozí prvek VSPackage správy zdrojového kódu, který se nastaví jako aktivní při restartu.

  Na rozdíl od předchozích verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] není restartování IDE jediným způsobem, jak přepínat VSPackage správy zdrojového kódu. Výběr VSPackage je automatický. Přepínání balíčků vyžaduje oprávnění uživatele systému Windows (nikoli správce nebo Power Users).

## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Funkce](../../extensibility/internals/source-control-vspackage-features.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Balíčky VSPackage](../../extensibility/internals/vspackages.md)