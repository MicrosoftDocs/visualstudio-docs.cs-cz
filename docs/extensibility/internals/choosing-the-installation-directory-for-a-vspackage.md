---
title: Volba instalačního adresáře pro VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ead19e9f50201ab795e3c3f68b661037d309d98d
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011902"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Volba instalačního adresáře pro VSPackage
VSPackage a jeho podpůrné soubory musí být v systému souborů uživatele. Umístění závisí na tom, jestli je VSPackage spravované nebo nespravované, vaše souběžné schéma správy verzí a volba uživatele.

## <a name="unmanaged-vspackages"></a>Nespravované VSPackage
 Nespravovaný VSPackage je server COM, který se dá nainstalovat do libovolného umístění. Informace o jeho registraci musí přesně odrážet jeho umístění. Uživatelské rozhraní instalačního programu (UI) by mělo poskytovat výchozí umístění jako podadresář `ProgramFilesFolder` hodnoty vlastnosti Instalační služba systému Windows. Například:

*&lt;Složkaprogramfiles &gt; \\ &lt; spolecnost &gt; \\ &lt; MyVSPackageProduct &gt; \V1.0\\*

 Uživatel by měl mít povoleno změnit výchozí adresář tak, aby vyhovoval uživatelům, kteří mají malý spouštěcí oddíl a chtějí instalovat aplikace a nástroje na jiný svazek.

 Pokud vaše souběžné schéma používá VSPackage se správou verzí, můžete k ukládání různých verzí použít podadresáře. Například:

 *&lt;Složkaprogramfiles &gt; \\ &lt; spolecnost &gt; \\ &lt; MyVSPackageProduct &gt; \\ v 1.0 \\ 2002\\*

 *&lt;Složkaprogramfiles &gt; \\ &lt; spolecnost &gt; \\ &lt; MyVSPackageProduct &gt; \\ v 1.0 \\ 2003\\*

 *&lt;Složkaprogramfiles &gt; \\ &lt; spolecnost &gt; \\ &lt; MyVSPackageProduct &gt; \\ v 1.0 \\ 2005\\*

## <a name="managed-vspackages"></a>Spravované VSPackage
 Spravované VSPackage se dají nainstalovat taky v libovolném umístění. Měli byste však zvážit, že byste je vždy nainstalovali do globální mezipaměti sestavení (GAC), aby se snížila doba načítání sestavení. Vzhledem k tomu, že spravované sady VSPackage jsou vždy silně pojmenované sestavení, jejich instalace v mezipaměti GAC znamená, že jejich ověření podpisu silného názvu trvá pouze v době instalace. Sestavení se silným názvem nainstalovaná jinde v systému souborů musí mít při každém načtení signatury ověřené. Při instalaci spravovaných VSPackage do GAC použijte přepínač **/Assembly je** nástroje RegPkg, který zapíše položky registru ukazující na silný název sestavení.

 Pokud nainstalujete spravované sady VSPackage do jiného umístění než GAC, postupujte podle předchozích rad pro nespravované sady VSPackage pro výběr hierarchií adresářů. Použijte přepínač **/codebase** nástroje RegPkg a zapište položky registru, které odkazují na cestu sestavení VSPackage.

 Další informace najdete v tématu [registrace a zrušení registrace VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Satelitní knihovny DLL
 Podle konvence, satelitní knihovny pro VSPackage, které obsahují prostředky pro konkrétní národní prostředí, jsou umístěny v podadresářích adresáře *VSPackage* . Podadresáře odpovídají hodnotám ID národního prostředí (LCID).

 Článek [Spravovat sady VSPackage](../../extensibility/managing-vspackages.md) označuje, že ovládací prvek položky registru, kde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve skutečnosti hledá satelitní knihovnu DLL VSPackage. Nicméně se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pokusí načíst satelitní knihovnu DLL v podadresáři s názvem pro hodnotu LCID v následujícím pořadí:

1. Výchozí LCID (Visual Studio LCID; například *\ 1033* pro angličtinu)

2. Výchozí LCID s výchozím podjazykem.

3. Systémové výchozí LCID.

4. Systémové výchozí LCID s výchozím podjazykem.

5. Angličtina USA (*. \ 1033* nebo *.\0x409*).

Pokud knihovna VSPackage DLL obsahuje prostředky a vstupní body registru **SatelliteDll\DllName** , [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pokusí se je načíst v uvedeném pořadí.

## <a name="see-also"></a>Viz také:
- [Volba mezi Shared a VSPackage se správou verzí](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Správa balíčků VSPackage](../../extensibility/managing-vspackages.md)
- [Správa registrace balíčku](/previous-versions/bb166783(v=vs.100))