---
title: Výběr instalačního adresáře pro balíček VSPackage | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709765"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>Výběr instalačního adresáře pro balíček VSPackage
VSPackage a jeho podpůrné soubory musí být v systému souborů uživatele. Umístění závisí na tom, zda je VSPackage spravované nebo nespravované, vaše schéma správy verzí vedle sebe a volba uživatele.

## <a name="unmanaged-vspackages"></a>Nespravované balíčky VSPackages
 Nespravovaný balíček VSPackage je server COM, který lze nainstalovat do libovolného umístění. Jeho registrační údaje musí přesně odrážet jeho umístění. Uživatelské rozhraní instalačního programu by mělo poskytovat výchozí umístění jako `ProgramFilesFolder` podadresář hodnoty vlastnosti Instalační služby systému Windows. Například:

*&lt;ProgramFilesFolder&gt;\\&lt;&gt;\\&lt;MyCompany MyVSPackageProduct&gt;\V1.0\\*

 Uživateli by mělo být umožněno změnit výchozí adresář tak, aby vyhovoval uživatelům, kteří mají malý spouštěcí oddíl a dávají přednost instalaci aplikací a nástrojů na jiný svazek.

 Pokud vaše schéma vedle sebe používá verzi VSPackage, můžete použít podadresáře k ukládání různých verzí. Například:

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2002\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2003\\*

 *&lt;ProgramFilesFolder&gt;\\&lt;MyCompany&gt;\\&lt;MyVSPackageProduct&gt;\\V1.0\\2005\\*

## <a name="managed-vspackages"></a>Spravované vspackages
 Spravované balíčky VSPackages lze také nainstalovat do libovolného umístění. Měli byste však zvážit jejich vždy jejich instalaci do globální mezipaměti sestavení (GAC), abyste zkrátili dobu načítání sestavení. Vzhledem k tomu, že spravované balíčky VSPackages jsou vždy sestavení s silným názvem, jejich instalace do gac znamená, že jejich ověření podpisu silného názvu trvá pouze v době instalace. Sestavení se silným názvem nainstalovaná jinde v systému souborů musí mít své podpisy ověřené při každém načtení. Při instalaci spravované VSPackages v GAC, použijte nástroj **/assembly** přepínač nástroje regpkg pro zápis položek registru ukazující na silný název sestavení.

 Pokud nainstalujete spravované Balíčky VSPackages do jiného umístění než GAC, postupujte podle dřívějších doporučení pro nespravované Balíčky VSPackages pro výběr hierarchií adresářů. Pomocí přepínače **/codebase nástroje /codebase** nástroje pro zápis položek registru směřujících na cestu sestavení VSPackage.

 Další informace naleznete v [tématu Register and Unregister VSPackages](../../extensibility/registering-and-unregistering-vspackages.md).

## <a name="satellite-dlls"></a>Satelitní knihovny DLL
 Podle konvence vSPackage satelitní knihovny DLL, které obsahují prostředky pro určité národní prostředí, jsou umístěny v podadresářích adresáře *VSPackage.* Podadresáře odpovídají hodnotám ID národního prostředí (LCID).

 Správa [VSPackages](../../extensibility/managing-vspackages.md) článek označuje, že [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] položky registru řídí, kde ve skutečnosti hledá satelitní DLL VSPackage. Pokusí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se však načíst satelitní dll v podadresáři pojmenované mj.

1. Výchozí soubor LCID (Visual Studio LCID; například *\1033* pro angličtinu)

2. Výchozí soubor LCID s výchozím podjazykem.

3. Výchozí systém LCID.

4. Výchozí systém LCID s výchozím podjazykem.

5. Americká angličtina (*.\1033* nebo *.\0x409*).

Pokud vaše dll VSPackage obsahuje prostředky a Položka registru **SatelliteDll\DllName** na něj odkazuje, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pokusí se je načíst ve výše uvedeném pořadí.

## <a name="see-also"></a>Viz také
- [Výběr mezi sdílenými a verzemi vs balíčků](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Správa balíčků VSPackage](../../extensibility/managing-vspackages.md)
- [Správa registrace balíčku](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
