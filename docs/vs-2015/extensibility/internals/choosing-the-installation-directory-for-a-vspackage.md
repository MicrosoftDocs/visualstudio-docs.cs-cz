---
title: Volba instalačního adresáře pro VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4100c045181f32e51abcc59116a69cad6cc33b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697250"
---
# <a name="choosing-the-installation-directory-for-a-vspackage"></a>Výběr instalačního adresáře pro balíček VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage a jeho podpůrné soubory musí být v systému souborů uživatele. Umístění závisí na tom, jestli je VSPackage spravované nebo nespravované, vaše souběžné schéma správy verzí a volba uživatele.  
  
## <a name="unmanaged-vspackages"></a>Nespravované VSPackage  
 Nespravovaný VSPackage je server COM, který se dá nainstalovat do libovolného umístění. Informace o jeho registraci musí přesně odpovídat jeho umístění. Uživatelské rozhraní instalačního programu (UI) by mělo poskytovat výchozí umístění jako podadresář vlastnosti Složkaprogramfiles Instalační služba systému Windows. Příklad:  
  
 Složkaprogramfiles MyCompany\MyVSPackageProduct\V1.0\  
  
 Uživatel by měl mít povoleno změnit výchozí adresář tak, aby vyhovoval uživatelům, kteří mají malý spouštěcí oddíl a chtějí instalovat aplikace a nástroje na jiný svazek.  
  
 Pokud vaše souběžné schéma používá VSPackage se správou verzí, můžete k ukládání různých verzí použít podadresáře. Příklad:  
  
 Složkaprogramfiles MyCompany\MyVSPackageProduct\V1.0\2002\  
  
 Složkaprogramfiles MyCompany\MyVSPackageProduct\V1.0\2003\  
  
 Složkaprogramfiles MyCompany\MyVSPackageProduct\V1.0\2005\  
  
## <a name="managed-vspackages"></a>Spravované VSPackage  
 Spravované VSPackage se dají nainstalovat taky v libovolném umístění. Měli byste však zvážit, že byste je vždy nainstalovali do globální mezipaměti sestavení (GAC), aby se snížila doba načítání sestavení. Vzhledem k tomu, že spravované sady VSPackage jsou vždy silně pojmenované sestavení, jejich instalace v mezipaměti GAC znamená, že jejich ověření podpisu silného názvu trvá pouze v době instalace. Sestavení se silným názvem nainstalovaná jinde v systému souborů musí mít při každém načtení signatury ověřené. Při instalaci spravovaných VSPackage do GAC použijte přepínač **/Assembly je** nástroje RegPkg, který zapíše položky registru ukazující na silný název sestavení.  
  
 Pokud nainstalujete spravované sady VSPackage do jiného umístění než GAC, postupujte podle předchozích rad pro nespravované sady VSPackage pro výběr hierarchií adresářů. Použijte přepínač **/codebase** nástroje RegPkg a zapište položky registru, které odkazují na cestu sestavení VSPackage.  
  
 Další informace najdete v tématu [registrace a zrušení registrace VSPackage](../../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="satellite-dlls"></a>Satelitní knihovny DLL  
 Podle konvence, satelitní knihovny pro VSPackage, které obsahují prostředky pro konkrétní národní prostředí, jsou umístěny v podadresářích adresáře VSPackage. Podadresáře odpovídají hodnotám ID národního prostředí (LCID).  
  
 [Správa sady VSPackage](../../extensibility/managing-vspackages.md) označuje, že ovládací prvek položky registru, kde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve skutečnosti hledá satelitní knihovnu DLL VSPackage. Nicméně se [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pokusí načíst satelitní knihovnu DLL v podadresáři s názvem pro hodnotu LCID v následujícím pořadí:  
  
1. Výchozí LCID (např. LCID, například \ 1033 pro angličtinu)  
  
2. Výchozí LCID s výchozím podjazykem.  
  
3. Systémové výchozí LCID.  
  
4. Systémové výchozí LCID s výchozím podjazykem.  
  
5. Angličtina USA (. \ 1033 nebo .\0x409).  
  
   Pokud knihovna VSPackage DLL obsahuje prostředky a vstupní body registru SatelliteDll\DllName, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pokusí se je načíst v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Volba mezi sdílenými a sesprávou verzí VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Správa VSPackage](../../extensibility/managing-vspackages.md)   
 [Registrace spravovaného balíčku](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
