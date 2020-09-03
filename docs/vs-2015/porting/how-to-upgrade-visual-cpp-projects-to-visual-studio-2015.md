---
title: 'Postupy: upgrade Visual C++ch projektů na Visual Studio 2015 | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278726"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Postupy: Upgrade projektů ve Visual C++ na Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poslední dokumentaci k sadě Visual Studio 2017 naleznete v tématu [Visual C++ Průvodce přenosem a upgradem](/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Při prvním otevření Visual C++ projektu, který byl vytvořen v dřívější verzi sady Visual Studio, může být zobrazena výzva k aktualizaci projektu. Zpráva s dotazem, zda chcete upgradovat na nejnovější verzi kompilátoru Visual C++ a knihovny. Možnosti pro upgrade závisí na verzi nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , která byla použita k vytvoření projektu.

 Můžete použít [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] k otevření, úpravám a sestavení [!INCLUDE[win8](../includes/win8-md.md)] projektů, které byly vytvořeny v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] , ale k vytvoření nového [!INCLUDE[win8](../includes/win8-md.md)] projektu, je nutné použít [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] . (Chcete-li vytvořit [!INCLUDE[win81](../includes/win81-md.md)] projekt, je nutné použít [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] .)

 Chcete-li vytvořit projekt s Windows 10, je nutné použít [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] .

 Pokud se vám nezobrazí výzva k aktualizaci projektu, nemusí být nutné provádět žádné kroky k upgradu projektu.

- Pokud byl projekt (. vcproj) vytvořen ve verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , která je starší než, je [!INCLUDE[vs2010](../includes/vs2010-md.md)] nutné projekt aktualizovat.

- Pokud byl projekt (. vcxproj) vytvořen v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ,  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] nebo [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] máte dvě možnosti:

  - Aktualizaci můžete přeskočit. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] načte projekt bez provedení změn, pokud má přístup k nástrojům Visual C++ v nástroji [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] s aktualizací SP1,  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] nebo [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] . Tento přístup můžete poskytnout instalací verze sady Visual Studio, ve které byl projekt vytvořen, na stejném počítači, který má [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] . Další informace najdete v části [instalace verzí sady Visual Studio vedle sebe](../install/install-visual-studio-versions-side-by-side.md).

  - Projekt můžete aktualizovat tak, že povolíte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] změny, které jsou popsány dále v tomto tématu. Pokud máte ve svém řešení více než jeden Visual C++ projekt, musíte aktualizovat všechny.

    > [!NOTE]
    > Pokud aktualizaci odmítnete při prvním zobrazení výzvy, můžete projekt aktualizovat později kliknutím na **Aktualizovat projekt VC + +** v nabídce **projekt** . Pokud se příkaz nezobrazí, není nutná aktualizace.

## <a name="upgrading-a-visual-c-project"></a>Upgrade projektu Visual C++
 Pokud povolíte [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] automatickou aktualizaci projektu, provedou se tyto změny:

- Změní projekt tak, aby používal [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] kompilátor a knihovny (PlatformToolset = VisualStudio v140).

- V případě [!INCLUDE[cppcli](../includes/cppcli-md.md)] projektů změní TargetFrameworkVersion na .NET Framework 4.5.2.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Pokračování v práci s vlastním PlatformToolset
 Chcete-li pokračovat v práci s vlastním PlatformToolset v nástroji [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] , musí být sada nástrojů umístěna pod%ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ v počítači x86 nebo v části% ProgramFiles (x86)% \ MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ v počítači x64. Informace o tom, jak vytvořit vlastní PlatformToolset, najdete v tématu věnovaném [nativnímu cílení na více platforem C++](https://blogs.msdn.com/b/vcblog/archive/2009/12/08/c-native-multi-targeting.aspx) na blogu týmu Visual C++.

## <a name="see-also"></a>Viz také
 [Visual C++ přenosů a upgradování Průvodce](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) přenosem a upgradem [, migrace a upgrade projektů sady Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
