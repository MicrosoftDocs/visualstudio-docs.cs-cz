---
title: Registrace a výběr (řízení zdrojového balíčku VSPackage) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d601aeca3864e47da77fd6418f4cfd3a5db1623
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834874"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrace a výběr (balíček VSPackage správy zdrojového kódu)
Ovládací prvek zdroje balíčku VSPackage musí být zaregistrovaný k vystavení tak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pokud se více než jeden ovládací prvek zdroje balíčku VSPackage zaregistruje, může uživatel vybrat které VSPackage načíst ve vhodných chvílích. Zobrazit [rozšíření VSPackages](../../extensibility/internals/vspackages.md) podrobné informace o rozšíření VSPackages a jak se zaregistrovat.  
  
## <a name="registering-a-source-control-package"></a>Registrace balíčku zdrojového ovládacího prvku  
 Zdrojový ovládací prvek balíček je zaregistrovaný tak, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí můžete najít a dotazů pro jeho podporované funkce. Toto je v souladu s zpoždění načítání schématu, ve kterém je vytvořena instance balíčku pouze při jeho funkce nebo příkazy jsou povinné nebo jsou explicitně požadována.  
  
 Rozšíření VSPackages umístit informace v klíči registru specifické pro verzi, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, kde *X* je číslo hlavní verze a *Y* je číslo podverze. Tento postup umožňuje podporují instalaci více verzí modulu vedle sebe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Uživatelského rozhraní (UI) podporuje výběru z několika nainstalovaný ovládací prvek moduly plug-in zdrojového kódu (prostřednictvím zdrojový ovládací prvek adaptér balíček) a také balíčků VSPackage správy zdrojového kódu. Může existovat pouze jeden modul plug-in správy zdrojů aktivní nebo VSPackage najednou. Ale jak je popsáno níže, integrované vývojové prostředí umožňuje přepínání mezi zdrojového ovládacího prvku moduly plug-in a rozšíření VSPackages prostřednictvím řešení na základě balíčku prohození mechanismus automatického. Existují některé požadavky ze strany správy zdrojového kódu VSPackage povolit tento mechanismus výběru.  
  
### <a name="registry-entries"></a>Položky registru  
 Zdrojový ovládací prvek balíček potřebuje tři soukromé identifikátory GUID:  
  
- Identifikátor GUID balíčku: Toto je hlavní identifikátor GUID pro balíček, který obsahuje implementaci ovládacího prvku zdroje (nazývané ID_Package v této části).  
  
- Identifikátor GUID správy zdrojového kódu: Toto je identifikátor GUID pro správu verzí používá k registraci ve službě Visual Studio pomocí zástupných procedur ovládací prvek zdroje balíčku VSPackage a slouží také jako kontextu uživatelského rozhraní příkaz identifikátor GUID. Službu správy zdrojových kódů GUID je zaregistrovaný pod správou zdrojových kódů identifikátor GUID. V tomto příkladu se nazývá modul správy zdrojových kódů GUID ID_SccProvider.  
  
- Zdrojový ovládací prvek služby GUID: Jedná se o privátní službu GUID používá sada Visual Studio (nazývané SID_SccPkgService v této části). Kromě toho zdrojový balíček ovládací prvek musí definovat jiné identifikátory GUID pro balíčky VSPackages, okna nástrojů, a tak dále.  
  
  Následující položky registru musí být provedené balíčku VSPackage správy zdrojového kódu:  
  
| Název klíče | Položky |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (výchozí) = rg_sz: {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (výchozí) = rg_sz:\<popisný název balíčku ><br /><br /> Služba = rg_sz: {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (výchozí) = rg_sz: #\<ID prostředku pro lokalizovaný název ><br /><br /> Balíček = rg_sz: {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Všimněte si, že název klíče, `SourceCodeControl`, je již využíván jiným [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a není k dispozici jako volba pro \<název_balíčku >.) | (výchozí) = rg_sz: {ID_Package} |
  
## <a name="selecting-a-source-control-package"></a>Vyberte zdrojový balíček ovládacího prvku  
 Několik založené na rozhraní API modulu Plug-in zdroje ovládacího prvku moduly plug-in a rozšíření VSPackages může současně zaregistrovat správy zdrojového kódu. Výběr modulu plug-in správy zdrojového kódu nebo balíčku VSPackage proces musíte zajistit, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načte modul plug-in nebo VSPackage v příslušnou dobu a můžete odložit načítání zbytečné komponent, dokud jsou povinné. Kromě toho [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musíte odebrat všechny uživatelského rozhraní od jiných neaktivní rozšíření VSPackages, včetně nabídek, dialogová okna a panely nástrojů a zobrazit uživatelské rozhraní pro aktivní VSPackage.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtení balíčku VSPackage správy zdrojového kódu při provádění kterékoli z následujících operací:  
  
- Otevření řešení (Pokud je řešení pod správou zdrojových kódů).  
  
   Při otevření řešení nebo projekt pod správou zdrojových kódů, rozhraní IDE způsobí, že správy zdrojového kódu VSPackage, která byla určena pro příslušné řešení, který se má načíst.  
  
- Některé příkazy ze zdrojového balíčku VSPackage provádějí.  
  
  Ovládací prvek zdroje balíčku VSPackage by se měly načíst všechny součásti, které potřebuje pouze v případě, že se ve skutečnosti má být použita (jinak známé jako zpožděného načtení).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Vzájemná záměna automatické řešení na základě balíčku VSPackage  
 Ručně odkládacího souboru správy zdrojového kódu rozšíření VSPackages prostřednictvím [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **možnosti** dialogového okna **správy zdrojových kódů** kategorie. Automatické řešení balíčků založená na vzájemné záměny znamená, že zdroj balíčku ovládací prvek, který je určený pro konkrétní řešení je automaticky nastaven na aktivní při otevření tohoto řešení. Každý balíček ovládací prvek zdroje by měly implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zpracovává přepínání mezi oba zdroje moduly plug-in správy (implementace rozhraní API modulu Plug-in zdroje ovládacího prvku) a balíčků VSPackage správy zdrojového kódu.  
  
 Přepnout na každém založené na rozhraní API modulu Plug-in zdroje ovládacího prvku se používá balíček adaptér ovládací prvek zdroj modulu plug-in. Proces přepínání zprostředkující zdrojový ovládací prvek adaptér balíček a určení, které plug-in správy zdrojových kódů musí být nastavena na aktivní nebo neaktivní je pro uživatele transparentní. Balíček adaptér je aktivní, vždy když žádné plug-in správy zdrojových kódů je aktivní. Přepínání mezi dvě hodnoty moduly plug-in ovládací prvek zdroje k jednoduše načítání a uvolňování knihovnu DLL modulu plug-in. Přepnutí do balíčku VSPackage správy zdrojového kódu, ale zahrnuje interakce s integrovaným vývojovým prostředím k načtení příslušné VSPackage.  
  
 Ovládací prvek zdroje balíčku VSPackage je volána, když je otevřené žádné řešení a klíče registru pro sady VSPackage je v souboru řešení. Po otevření řešení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hodnotu registru vyhledá a načte odpovídající zdrojového balíčku VSPackage. Všechny správy zdrojového kódu rozšíření VSPackages musí mít položky registru je popsáno výše. Řešení, které je pod správou zdrojových kódů je označena jako jsou spojeny s konkrétní zdrojového balíčku VSPackage. Musí implementovat balíčků VSPackage správy zdrojového kódu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> povolit automatické řešení na základě balíčku VSPackage prohození.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio uživatelského rozhraní pro výběr balíčku a přepínání  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poskytuje uživatelské rozhraní pro balíčku VSPackage správy zdrojového kódu a výběr modulu plug-in v **možnosti** dialogového okna **správy zdrojových kódů** kategorie. Umožňuje uživateli vybrat aktivní plug-in správy zdrojových kódů nebo VSPackage. Rozevírací seznam obsahuje:  
  
- Všechny nainstalované balíčky správy zdrojového kódu  
  
- Všechny nainstalované moduly plug-in programu zdrojového ovládacího prvku  
  
- "Žádná" možnost, která zakáže zdrojového kódu  
  
  Je viditelný pouze v uživatelském rozhraní podle výběru ovládacího prvku aktivní zdrojové. Výběr balíčku VSPackage skryje uživatelské rozhraní pro předchozí VSPackage a zobrazuje uživatelské rozhraní pro nový uzel. Aktivní VSPackage je vybrána na základě jednotlivých uživatelů. Pokud má několik kopií [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] otevřete souběžně, potenciálně každé z nich můžete použít jiné aktivní VSPackage. Pokud více uživatelům přihlášení do stejného počítače, každý uživatel může mít samostatné instance [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] otevřete, každý s jinou aktivní VSPackage. Pokud více instancí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zavřou uživatelem, správy zdrojového kódu VSPackage, který byl aktivní pro poslední otevřít řešení stane výchozí zdrojového balíčku VSPackage nastavit aktivní při restartování.  
  
  Na rozdíl od předchozích verzí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], restartování integrovaného vývojového prostředí již není jediným způsobem, jak přepnout balíčků VSPackage správy zdrojového kódu. Výběr balíčku VSPackage je automatické. Přepínání balíčky vyžaduje oprávnění uživatele Windows (ne správce nebo Power Users).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Funkce](../../extensibility/internals/source-control-vspackage-features.md)   
 [Vytvoření modulu Plug-in správy zdrojového kódu](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Balíčky VSPackage](../../extensibility/internals/vspackages.md)