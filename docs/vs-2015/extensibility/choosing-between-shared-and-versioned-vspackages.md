---
title: Volba mezi sdíleným a Verzovaným rozšířením VSPackages | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9fcae5b736310424f220d08aefa4e061e1f6c860
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756828"
---
# <a name="choosing-between-shared-and-versioned-vspackages"></a>Volba mezi sdíleným a verzovaným rozšířením VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Různé verze sady Visual Studio můžou existovat společně na stejném počítači. Rozšíření VSPackages může podporovat všechny kombinace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verze.  
  
 Povolíte-souběžnými instalacemi balíčků VSPackage pomocí kteréhokoliv z dvou strategií, sdílené strategii nebo systémovou správou verzí strategie. Obě podle přítomnosti více verzí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a související verze [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 Ve sdílené strategie je zaregistrovaný jednoho balíčku VSPackage pro použití ve více verzích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Při použití strategie označené verzí jsou nainstalovány více knihoven dll balíčku VSPackage, jeden pro každou verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , kterou podporujete.  
  
## <a name="shared-vspackages"></a>Sdílené rozšíření VSPackages  
 Použití sdílené VSPackage je vhodné při použití stejného balíčku VSPackage ve více verzích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pro implementaci sdíleného VSPackage, je nutné provést následující kroky:  
  
-   Ujistěte se, vaši VSPackage kompatibilní s více verzemi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dva způsoby, jak udělat proto jsou k dispozici:  
  
    -   Omezit vašeho balíčku VSPackage pomocí pouze funkce nejstarší verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , kterou podporujete.  
  
    -   Program vašeho balíčku VSPackage umožní reagovat na verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve kterém je spuštěná. Pak v případě dotazů pro novější služby selžou, vašeho balíčku VSPackage můžou nabízet další služby, které jsou podporovány ve starších verzích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Zaregistrujte vašeho balíčku VSPackage odpovídajícím způsobem. Další informace najdete v tématu [registrace balíčku VSPackage](../extensibility/internals/vspackage-registration.md) a [spravovat registrace balíčku VSPackage](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).  
  
-   Registrace přípon souborů odpovídajícím způsobem. Další informace najdete v tématu [registrace přípony názvů souborů pro nasazení vedle sebe](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Vytvořit instalační službu, která nasadí vašeho balíčku VSPackage pro příslušnou verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Další informace najdete v tématu [instalace rozšíření VSPackages s Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) a [Správa komponent](../extensibility/internals/component-management.md).  
  
-   Vyřešení problému registrace kolizí. Další informace najdete v tématu [registrace balíčku VSPackage](../extensibility/internals/vspackage-registration.md).  
  
-   Ujistěte se, že soubory sdíleným a verzovaným respektovat počítání odkazů ke umožňují bezpečnou instalaci a odebrání více verzí. Další informace najdete v tématu [Správa komponent](../extensibility/internals/component-management.md).  
  
## <a name="versioned-vspackages"></a>Verze rozšíření VSPackages  
 V rámci verze balíčku VSPackage strategie, vytvoříte jednu VSPackage pro každou verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , kterou podporujete. To je vhodné, pokud očekáváte, že chcete využít výhod služeb poskytovaných novějších verzích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], protože každý VSPackage můžete rozvíjet aniž by to ovlivnilo ostatní. Označené verzí strategie vytváření více binárních souborů, z jediného základu kódu nebo z více základních tříd nezávislý kód, však může za následek další počáteční vývoj než sdílený strategie. Navíc další nastavení může být vyžadován, protože musíte vytvořit buď samostatný instalační program pro každou verzi nebo jeden instalační program, který zjistí verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , které jsou nainstalovány a, která podporuje vaše VSPackage.  
  
## <a name="binary-compatibility"></a>Binární kompatibilita  
 Obecně platí binární kompatibilitu umožňuje rozšíření VSPackages nativního kódu byly vyvinuty v sadě starších verzích sady Visual Studio ke spuštění v pozdějších verzích sady Visual Studio. Nicméně existují tři důležité výjimky:  
  
- Pokud vaše VSPackage závisí na konkrétní verzi modulu common language runtime a pak ho musíte určit, kterou verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] běží.  
  
- VSPackage může mít závislost na konkrétní funkce jiné VSPackage nebo jiného produktu. V důsledku toho můžete spustit sady VSPackage, pouze pokud je splněna závislost.  
  
- VSPackage by mohly mít dopad opravu zabezpečení v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aktualizace service pack nebo novější verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. V takových případech VSPackage vyvinuté pomocí starší verze [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] nemusí spouštět ve verzích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po opravu zabezpečení. Můžete však sestavte svůj balíček pomocí novější verze znovu a ho také spustit v dřívějších verzích.  
  
  Spravovaná rozšíření VSPackages musí být sestaveny pomocí verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] , které odpovídají cílovou verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  Kromě plánování binární kompatibilitu pro vaše binární soubory balíčku VSPackage, můžete také by měl zvažte řešení a projektu formátů souborů. Pokud vaše VSPackage vytvoří nový typ projektu, musíte se rozhodnout, zda lze spustit v pouze jednu verzi nebo ve více verzích [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Další informace najdete v tématu [upgrade projektů vlastní](../misc/upgrading-custom-projects.md).  
  
## <a name="see-also"></a>Viz také  
 [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)   
 [Správa komponent](../extensibility/internals/component-management.md)

