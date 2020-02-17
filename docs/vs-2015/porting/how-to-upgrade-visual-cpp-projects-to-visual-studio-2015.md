---
title: 'Postupy: Upgrade projektů Visual C++ pro Visual Studio 2015 | Dokumentace Microsoftu'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 23461fb1927cfcbf738d2dbcb82e3977b3be265a
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278726"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Postupy: Upgrade projektů ve Visual C++ na Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poslední dokumentaci k sadě Visual Studio 2017 najdete v tématu [Průvodce pro C++ přenos a upgrade vizuálů](/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Při prvním otevření projektu Visual C++, který byl vytvořen v dřívější verzi sady Visual Studio, které může zobrazit výzva k aktualizaci projektu. Zpráva s dotazem, zda chcete provést upgrade na nejnovější verzi kompilátoru jazyka Visual C++ a knihoven. Možnosti pro upgrade závisí na verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], která byla použita k vytvoření projektu.

 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] můžete použít k otevření, úpravám a sestavení [!INCLUDE[win8](../includes/win8-md.md)] projektů, které byly vytvořeny v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], ale k vytvoření nového projektu [!INCLUDE[win8](../includes/win8-md.md)] je nutné použít [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. (Chcete-li vytvořit projekt [!INCLUDE[win81](../includes/win81-md.md)], je nutné použít [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].)

 Chcete-li vytvořit projekt s Windows 10, je nutné použít [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)].

 Pokud se zobrazí výzva k aktualizaci projektu, nemáte k ničemu upgradovat projekt.

- Pokud byl projekt (. vcproj) vytvořen ve verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], která je starší než [!INCLUDE[vs2010](../includes/vs2010-md.md)], je nutné projekt aktualizovat.

- Pokud byl projekt (. vcxproj) vytvořen v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]nebo [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] máte dvě možnosti:

  - Aktualizaci můžete přeskočit. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] načte projekt bez provedení změn, pokud má přístup k vizuálním C++ nástrojům v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] s aktualizací SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]nebo [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Tento přístup můžete poskytnout instalací verze sady Visual Studio, ve které byl projekt vytvořen, na stejném počítači, který má [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]. Další informace najdete v části [instalace verzí sady Visual Studio vedle sebe](../install/install-visual-studio-versions-side-by-side.md).

  - Projekt můžete aktualizovat tím, že povolíte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] provádění změn, které jsou popsány dále v tomto tématu. Pokud máte více než jeden projekt Visual C++ ve vašem řešení, musíte aktualizovat všechny z nich.

    > [!NOTE]
    > Pokud aktualizaci odmítnete při prvním zobrazení výzvy, můžete projekt aktualizovat později kliknutím na **Aktualizovat projekt VC + +** v nabídce **projekt** . Pokud tento příkaz nezobrazí, není aktualizace požadována.

## <a name="upgrading-a-visual-c-project"></a>Upgrade projektu Visual C++
 Pokud povolíte [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] automaticky aktualizovat projekt, provedou se tyto změny:

- Změní projekt tak, aby používal kompilátor [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] a knihovny (PlatformToolset = VisualStudio v140).

- U [!INCLUDE[cppcli](../includes/cppcli-md.md)] projektů změní TargetFrameworkVersion na .NET Framework 4.5.2.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Pokračovat v práci s vlastní sadou PlatformToolset
 Chcete-li pokračovat v práci s vlastním PlatformToolset v [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], musí být sada nástrojů umístěna pod%ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ v počítači x86 nebo v části% ProgramFiles (x86)% \ MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ v počítači x64. Informace o tom, jak vytvořit vlastní PlatformToolset, najdete v tématu [ C++ nativní cílení na více](https://blogs.msdn.com/b/vcblog/archive/2009/12/08/c-native-multi-targeting.aspx) platforem C++ na blogu týmu vizuálů.

## <a name="see-also"></a>Viz také
 Portování [a upgrade průvodce pro C++ vizuální](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) přenos [, migraci a upgrade projektů sady Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
