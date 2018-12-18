---
title: Volba mezi sdíleným a Verzovaným rozšířením VSPackages | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3bb3cebb9cdc00f6e4ef486ef6330cf2b18c6dc1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817299"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Výběr mezi sdíleným a verzovaným rozšířením VSPackages
Různé verze sady Visual Studio můžou existovat společně na stejném počítači. Rozšíření VSPackages může podporovat všechny kombinace [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verze.  
  
 Povolíte-souběžnými instalacemi balíčků VSPackage pomocí kteréhokoliv z dvou strategií, sdílené strategii nebo systémovou správou verzí strategie. Obě podle přítomnosti více verzí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a související verze [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Ve sdílené strategie je zaregistrovaný jednoho balíčku VSPackage pro použití ve více verzích [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Při použití strategie označené verzí jsou nainstalovány více knihoven dll balíčku VSPackage, jeden pro každou verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , kterou podporujete.  
  
## <a name="shared-vspackages"></a>Sdílené rozšíření VSPackages  
 Použití sdílené VSPackage je vhodné při použití stejného balíčku VSPackage ve více verzích [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pro implementaci sdíleného VSPackage, je nutné provést následující kroky:  
  
- Ujistěte se, vaši VSPackage kompatibilní s více verzemi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dva způsoby, jak udělat proto jsou k dispozici:  
  
  - Omezit vašeho balíčku VSPackage pomocí pouze funkce nejstarší verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , kterou podporujete.  
  
  - Program vašeho balíčku VSPackage umožní reagovat na verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve kterém je spuštěná. Pak v případě dotazů pro novější služby selžou, vašeho balíčku VSPackage můžou nabízet další služby, které jsou podporovány ve starších verzích [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- Zaregistrujte vašeho balíčku VSPackage odpovídajícím způsobem. Další informace najdete v tématu [registrace balíčku VSPackage](../extensibility/internals/vspackage-registration.md) a [registrace balíčku VSPackage spravované](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
- Registrace přípon souborů odpovídajícím způsobem. Další informace najdete v tématu [registrace přípony názvů souborů pro nasazení vedle sebe](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Vytvořit instalační službu, která nasadí vašeho balíčku VSPackage pro příslušnou verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Další informace najdete v tématu [instalace balíčků VSPackage pomocí Instalační služby systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) a [Správa komponent](../extensibility/internals/component-management.md).  
  
- Vyřešení problému registrace kolizí. Další informace najdete v tématu [registrace balíčku VSPackage](../extensibility/internals/vspackage-registration.md).  
  
- Ujistěte se, že soubory sdíleným a verzovaným respektovat počítání odkazů ke umožňují bezpečnou instalaci a odebrání více verzí. Další informace najdete v tématu [Správa komponent](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Verze rozšíření VSPackages  
 V rámci verze balíčku VSPackage strategie, vytvoříte jednu VSPackage pro každou verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , kterou podporujete. To je vhodné, pokud očekáváte, že chcete využít výhod služeb poskytovaných novějších verzích [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], protože každý VSPackage můžete rozvíjet aniž by to ovlivnilo ostatní. Označené verzí strategie vytváření více binárních souborů, z jediného základu kódu nebo z více základních tříd nezávislý kód, však může za následek další počáteční vývoj než sdílený strategie. Navíc další nastavení může být vyžadován, protože musíte vytvořit buď samostatný instalační program pro každou verzi nebo jeden instalační program, který zjistí verze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , které jsou nainstalovány a, která podporuje vaše VSPackage.  
  
## <a name="binary-compatibility"></a>Binární kompatibilita  
 Obecně platí binární kompatibilitu umožňuje rozšíření VSPackages nativního kódu byly vyvinuty v sadě starších verzích sady Visual Studio ke spuštění v pozdějších verzích sady Visual Studio. Nicméně existují tři důležité výjimky:  
  
- Pokud vaše VSPackage závisí na konkrétní verzi modulu common language runtime a pak ho musíte určit, kterou verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] běží.  
  
- VSPackage může mít závislost na konkrétní funkce jiné VSPackage nebo jiného produktu. V důsledku toho můžete spustit sady VSPackage, pouze pokud je splněna závislost.  
  
- VSPackage by mohly mít dopad opravu zabezpečení v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aktualizace service pack nebo novější verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. V takových případech VSPackage vyvinuté pomocí starší verze [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] nemusí spouštět ve verzích [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] po opravu zabezpečení. Můžete však sestavte svůj balíček pomocí novější verze znovu a ho také spustit v dřívějších verzích.  
  
  Spravovaná rozšíření VSPackages musí být sestaveny pomocí verze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] , které odpovídají cílovou verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
  Kromě plánování binární kompatibilitu pro vaše binární soubory balíčku VSPackage, můžete také by měl zvažte řešení a projektu formátů souborů. Pokud vaše VSPackage vytvoří nový typ projektu, musíte se rozhodnout, zda lze spustit v pouze jednu verzi nebo ve více verzích [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Další informace najdete v tématu [upgrade vlastních projektů](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).  
  
## <a name="see-also"></a>Viz také:  
 [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Správa komponent](../extensibility/internals/component-management.md)