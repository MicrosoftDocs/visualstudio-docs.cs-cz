---
title: Výběr mezi sdílenými a s verzemi vspackages | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739888"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Výběr mezi sdílenými a verzemi vs balíčků
Různé verze sady Visual Studio mohou existovat společně ve stejném počítači. VSPackages může podporovat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] libovolnou kombinaci verzí.

 Můžete povolit souběžné instalace VSPackages prostřednictvím jedné ze dvou strategií, sdílené strategie nebo strategie verze. Oba pojmout přítomnost více [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verzí a přidružené verze rozhraní .NET Framework.

 Ve sdílené strategii je jeden VSPackage registrován pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]použití ve více verzích aplikace . Ve strategii verze jsou nainstalovány více Knihovny DLL Balíčku, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jeden pro každou verzi, kterou podporujete.

## <a name="shared-vspackages"></a>Sdílené vspackages
 Použití sdíleného balíčku VSPackage je vhodné při použití stejného [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]balíčku VSPackage ve více verzích aplikace . Chcete-li implementovat sdílený balíček VSPackage, musíte provést následující kroky:

- Umožňuje, aby byl váš Balíček [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage kompatibilní s více verzemi aplikace . K dispozici jsou dva způsoby:

  - Omezte svůj VSPackage na použití [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pouze funkce nejstarší verze, které podporujete.

  - Program VSPackage přizpůsobit verzi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve kterém je spuštěn. Pokud se pak dotazy na novější služby nezdaří, může váš VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nabídnout další služby, které jsou podporovány ve starších verzích aplikace .

- Zaregistrujte svůj VSPackage odpovídajícím způsobem. Další informace naleznete [v tématu Registrace balíčku VSPackage](../extensibility/internals/vspackage-registration.md) a [Správa Registrace VSPackage](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Zaregistrujte přípony souborů odpovídajícím způsobem. Další informace naleznete v [tématu Registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Vytvořte instalační program, který nasazuje váš [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Balíček VSPackage pro příslušné verze aplikace . Další informace naleznete [v tématu Instalace balíčků VSPackages s Instalační službou systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) a Správa [součástí](../extensibility/internals/component-management.md).

- Řešit problém registračních kolizí. Další informace naleznete v [tématu VSPackage registrace](../extensibility/internals/vspackage-registration.md).

- Ujistěte se, že sdílené soubory i soubory s verzí respektují počítání odkazů, aby bylo možné bezpečně instalaci a odebrání více verzí. Další informace naleznete [v tématu Správa komponent](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>Balíčky VSs s verzí
 V rámci strategie VSPackage s verzí vytvoříte jeden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage pro každou verzi, kterou podporujete. To je vhodné, pokud očekáváte využít služeb poskytovaných [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]novější verze aplikace , protože každý VSPackage se může vyvíjet bez ovlivnění ostatních. Strategie vytváření více binárních souborů s verzí, buď z jednoho základu kódu, nebo z více nezávislých základů kódu, však může znamenat více počátečního vývoje než sdílená strategie. Také může být vyžadována další instalační práce, protože je nutné vytvořit samostatné nastavení pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] každou verzi nebo jednu instalaci, která zjistí verze, které jsou nainstalovány a které váš VSPackage podporuje.

## <a name="binary-compatibility"></a>Binární kompatibilita
 Binární kompatibilita obecně umožňuje spuštění nativních balíčků VSPackages vyvinutých s dřívějšími verzemi sady Visual Studio v novějších verzích sady Visual Studio. Existují však tři důležité výjimky:

- Pokud váš VSPackage spoléhá na konkrétní verzi za běhu společného jazyka, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pak musí určit, ve které verzi je spuštěna.

- VSPackage může mít závislost na konkrétní funkci jiného VSPackage nebo jiného produktu. V důsledku toho VSPackage lze spustit pouze v případě, že je splněna závislost.

- Balíček VSPackage může být ovlivněn [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opravou zabezpečení v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]aktualizaci Service Pack nebo novější verzi aplikace . V těchto případech VSPackage vyvinutý s dřívější [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] verzí nemusí být spuštěna ve verzích [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] po použití opravy zabezpečení. Balíček však můžete znovu sestavit s novější verzí a nechat jej spustit také v dřívějších verzích.

  Spravované balíčky VSPackages musí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] být [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] sestaveny pomocí verze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]aplikace a které odpovídají cílové verzi aplikace .

  Kromě plánování binární kompatibility binárních souborů VSPackage byste měli také zvážit formáty souborů řešení a projektu. Pokud váš VSPackage vytvoří nový typ projektu, musíte se rozhodnout, zda jej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]lze spustit pouze v jedné verzi nebo ve více verzích aplikace . Další informace naleznete v [tématu Upgrade vlastních projektů](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Viz také
- [Instalace balíčků VSPackages pomocí Instalační služby systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Správa komponent](../extensibility/internals/component-management.md)
