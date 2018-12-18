---
title: 'Postupy: Upgrade projektů Visual C++ pro Visual Studio 2015 | Dokumentace Microsoftu'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 493b96d4c66c35a242efd4957288d215ab2877ed
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063286"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Postupy: Upgrade projektů ve Visual C++ na Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci pro sadu Visual Studio 2017 najdete v tématu [průvodce Visual C++ přenosem a upgradováním](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Při prvním otevření projektu Visual C++, který byl vytvořen v dřívější verzi sady Visual Studio, které může zobrazit výzva k aktualizaci projektu. Zpráva s dotazem, zda chcete provést upgrade na nejnovější verzi kompilátoru jazyka Visual C++ a knihoven. Možnosti pro upgrade závisí na verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , která byla použita k vytvoření projektu.

 Můžete použít [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] otevřít, upravit a sestavit [!INCLUDE[win8](../includes/win8-md.md)] projekty, které byly vytvořeny v [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], ale k vytvoření nového [!INCLUDE[win8](../includes/win8-md.md)] projektu, je nutné použít [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. (Chcete-li vytvořit [!INCLUDE[win81](../includes/win81-md.md)] projektu, je nutné použít [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].)

 Vytvoření projektu Windows 10, je nutné použít [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)].

 Pokud se zobrazí výzva k aktualizaci projektu, nemáte k ničemu upgradovat projekt.

-   Pokud byl projekt (.vcproj) byl vytvořen ve verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , která je starší než [!INCLUDE[vs2010](../includes/vs2010-md.md)], je nutné aktualizovat projekt.

-   Pokud byl projekt (.vcxproj) vytvořen v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], nebo [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] máte dvě možnosti:

    -   Aktualizaci můžete přeskočit. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] načte projekt bez provedení změn, pokud má přístup k nástrojům aplikace Visual C++ v [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] s aktualizací SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], nebo [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Tento přístup můžete poskytnout instalací verze Visual Studio, která projekt byl vytvořen s ve stejném počítači, který má [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]. Další informace najdete v tématu [instalaci verzí sady Visual Studio Side-by-Side](../install/install-visual-studio-versions-side-by-side.md).

    -   Můžete aktualizovat projekt tím, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] provést změny, které jsou popsány dále v tomto tématu. Pokud máte více než jeden projekt Visual C++ ve vašem řešení, musíte aktualizovat všechny z nich.

        > [!NOTE]
        >  Pokud aktualizaci odmítnete při první výzvě, můžete aktualizovat projekt později výběrem **aktualizovat projekt VC ++** na **projektu** nabídky. Pokud tento příkaz nezobrazí, není aktualizace požadována.

## <a name="upgrading-a-visual-c-project"></a>Upgrade projektu Visual C++
 Pokud je povoleno [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] automaticky aktualizovat projekt, budou provedeny tyto změny:

-   Změní projekt tak, aby používala [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] kompilátor a knihovny (PlatformToolset = VisualStudio v140).

-   Pro [!INCLUDE[cppcli](../includes/cppcli-md.md)] projekty, změní TargetFrameworkVersion na .NET Framework 4.5.2.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Pokračovat v práci s vlastní sadou PlatformToolset
 Pokud chcete pokračovat v práci s vlastním parametrem PlatformToolset v [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], sada nástrojů se musí nacházet v části %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ v x x86 strojově, nebo v umístění % ProgramFiles (x86)%\MSBuild\ Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ x x64 počítače. Informace o tom, jak vytvořit vlastní PlatformToolset naleznete v tématu [cílení na více verzí v nativním C++](http://go.microsoft.com/fwlink/?LinkId=248587) na blogu týmu Visual C++.

## <a name="see-also"></a>Viz také
 [Visual C++ Průvodce přenosem a upgradem](http://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [přenosy, migrace a upgrade projektů sady Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
