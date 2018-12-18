---
title: Instalace sady Visual Studio SDK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- visual-studio-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e5546b07ef9917590daa573efd99377339412c7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793552"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalace sady Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalace sady Visual Studio SDK jako součást instalace sady Visual Studio  
 Pokud chcete zahrnout VSSDK instalaci sady Visual Studio, musíte provést vlastní instalaci.  
  
> [!NOTE]
>  V spustitelného souboru instalace sady Visual Studio SDK nazývá **Visual Studio Extensibility Tools**.  
  
1.  Spusťte instalaci sady Visual Studio 2015. Můžete instalaci libovolné edice sady Visual Studio s výjimkou Express.  
  
2.  Na první obrazovce vyberte **vlastní**, nikoli **výchozí**. Klikněte na tlačítko **Další**.  
  
3.  Měli byste vidět stromové zobrazení vlastní funkce. Otevřít **běžné nástroje**. Měli byste vidět **Visual Studio Extensibility Tools** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4.  Zkontrolujte **Visual Studio Extensibility Tools** , pak klikněte na tlačítko **Další** a pokračovat v instalaci.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalace sady Visual Studio SDK po instalaci sady Visual Studio  
 Pokud se rozhodnete nainstalovat Visual Studio SDK po dokončení instalace sady Visual Studio, postupujte podle následujícího postupu:  
  
1.  Přejděte na **ovládací panely / programy nebo programy a funkce**a vyhledejte **Visual Studio 2015**. Můžete nainstalovat sadu Visual Studio SDK pro všechny edice kromě Express sady Visual Studio 2015.  
  
2.  Klikněte pravým tlačítkem na **Visual Studio 2015**a potom klikněte na tlačítko **změnu**. Zobrazí se stránka instalace.  
  
3.  Postupujte stejným způsobem jako v **instalace sady Visual Studio SDK jako součást Visual Studio Installation** výše.  
  
4.  Klikněte na tlačítko **Visual Studio Extensibility Tools** odkaz a nainstalujte sadu Visual Studio SDK.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalace sady Visual Studio SDK v rámci řešení  
 Pokud otevřete řešení s projektem rozšíření bez první instalace VSSDK vyzve čárku zvýrazněné informace výše v Průzkumníku řešení. Měl by vypadat nějak takto:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalace sady Visual Studio SDK z příkazového řádku  
 VSSDK můžete nainstalovat z příkazového řádku pomocí **/installselectableitems** přepnout pomocí instalačního programu sady Visual Studio. Podrobnosti o používání parametrů příkazového řádku pomocí instalačního programu najdete v tématu [instalace sady Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Tady je postup instalace VSSDK tiše pomocí instalačního programu sady Visual Studio 2015 Community:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Všimněte si, že je nutné použít instalační program sady Visual Studio, který odpovídá vaší nainstalované verzi sady Visual Studio. Například pokud máte v počítači nainstalovaný Visual Studio Enterprise, musíte spustit instalační program sady Visual Studio Enterprise (vs_enterprise.exe).







