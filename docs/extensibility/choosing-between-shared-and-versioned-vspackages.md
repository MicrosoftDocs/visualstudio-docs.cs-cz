---
title: Volba mezi Shared a VSPackage se správou verzí | Microsoft Docs
description: Přečtěte si o souběžných instalacích VSPackage prostřednictvím sdílených nebo verzí sady Visual Studio a .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90acdde2c365effd189efe4437b5e41c39f494b0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949633"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Volba mezi Shared a VSPackage se správou verzí
V jednom počítači mohou existovat různé verze sady Visual Studio. Sady VSPackage můžou podporovat jakoukoli kombinaci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verzí.

 Můžete povolit souběžné instalace VSPackage prostřednictvím jedné ze dvou strategií, sdílené strategie nebo strategie se správou verzí. Jak přizpůsobit přítomnost více verzí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a přidružených verzí .NET Framework.

 Ve sdílené strategii je jeden VSPackage zaregistrován pro použití v několika verzích nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . V strategii s verzemi jsou nainstalovány více knihoven DLL sady VSPackage, jednu pro každou verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , kterou podporujete.

## <a name="shared-vspackages"></a>Sdílené VSPackage
 Použití sdíleného balíčku VSPackage je vhodné při použití stejného balíčku VSPackage v několika verzích nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Chcete-li implementovat sdílený VSPackage, je nutné provést následující kroky:

- Vyjistěte, aby byl váš VSPackage kompatibilní s více verzemi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . K dispozici jsou dva způsoby, jak to udělat:

  - Omezte sadu VSPackage na používání jenom těch funkcí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , které jsou pro vás podporovány.

  - Naprogramujte VSPackage, abyste se přizpůsobili verzi nástroje, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve které je spuštěná. Pokud pak selže dotaz na novější služby, může být VSPackage nabízet další služby, které jsou podporovány ve starších verzích nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Zaregistrujte VSPackage správně. Další informace najdete v tématu [Registrace VSPackage](../extensibility/internals/vspackage-registration.md) a [spravovaná registrace VSPackage](/previous-versions/bb166783(v=vs.100)).

- Zaregistrujte přípony souborů odpovídajícím způsobem. Další informace najdete v tématu [registrace přípon názvů souborů pro souběžná nasazení](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Vytvořte instalační program, který nasadí VSPackage pro příslušné verze nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Další informace najdete v tématu [Instalace VSPackage pomocí Instalační služba systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) a [správy součástí](../extensibility/internals/component-management.md).

- Řeší potíže s kolize registrací. Další informace najdete v tématu [Registrace VSPackage](../extensibility/internals/vspackage-registration.md).

- Zajistěte, aby sdílené i soubory se správou verzí dodržovaly počítání odkazů, aby bylo možné bezpečnou instalaci a odebrání více verzí. Další informace najdete v tématu [Správa součástí](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>VSPackage se správou verzí
 V rámci strategie verze balíčku VSPackage vytvoříte jednu sadu VSPackage pro každou verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , kterou podporujete. To je vhodné, pokud očekáváte, že budete využívat služby poskytované novějšími verzemi nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , protože každý VSPackage se může vyvíjet bez ovlivnění ostatních. Strategie verze vytváření více binárních souborů, buď z jednoho základu kódu nebo z několika nezávislých základních kódů, však může způsobit pokročilejší vývoj než sdílená strategie. Navíc může být nutné provést další práci s nastavením, protože je nutné vytvořit samostatnou instalaci pro každou verzi nebo jedno nastavení, které detekuje nainstalované verze nástroje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a kterou VSPackage podporuje.

## <a name="binary-compatibility"></a>Binární kompatibilita
 Obecně binární kompatibilita umožňuje, aby byly vyvinuty sady VSPackage nativního kódu s předchozími verzemi sady Visual Studio, aby běžely v novějších verzích sady Visual Studio. Existují však tři důležité výjimky:

- Pokud vaše VSPackage spoléhá na konkrétní verzi modulu CLR (Common Language Runtime), musí určit, ve které verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] je spuštěná.

- VSPackage může mít závislost na konkrétní funkci jiného VSPackage nebo jiného produktu. V důsledku toho může být VSPackage spuštěn pouze v případě, že je závislost splněna.

- Sada VSPackage může mít vliv na opravu zabezpečení v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aktualizaci Service Pack nebo v novější verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . V těchto případech může být VSPackage vyvinutý pomocí starší verze nástroje [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Nespuštěn v verzích [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] po použití opravy zabezpečení. Balíček ale můžete znovu sestavit v novější verzi a nechat ho také běžet v dřívějších verzích.

  Spravované sady VSPackage musí být sestaveny pomocí verze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] , která odpovídá cílové verzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  Kromě plánování binární kompatibility pro binární soubory VSPackage byste měli také zvážit formáty souborů řešení a projektu. Pokud VSPackage vytvoří nový typ projektu, je nutné rozhodnout, zda může běžet pouze v jedné verzi nebo ve více verzích [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Další informace najdete v tématu [Upgrade vlastních projektů](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Viz také
- [Instalace VSPackage pomocí Instalační služba systému Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Správa součástí](../extensibility/internals/component-management.md)