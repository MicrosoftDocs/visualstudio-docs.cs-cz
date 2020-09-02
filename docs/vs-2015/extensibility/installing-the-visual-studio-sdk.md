---
title: Instalace sady Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: visual-studio-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88a6266a3f5910def0bf5041a37f89c2b3d67416
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64858696"
---
# <a name="installing-the-visual-studio-sdk"></a>Instalace sady Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později.  
  
## <a name="installing-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalace sady Visual Studio SDK jako součást instalace sady Visual Studio  
 Pokud byste chtěli zahrnout VSSDK do instalace sady Visual Studio, musíte provést vlastní instalaci.  
  
> [!NOTE]
> V instalačním spustitelném souboru se sada Visual Studio SDK nazývá **Visual Studio Extensibility Tools**.  
  
1. Spusťte instalaci sady Visual Studio 2015. Můžete nainstalovat libovolnou edici sady Visual Studio s výjimkou expresního.  
  
2. Na první obrazovce vyberte možnost **vlastní**, **nevýchozí**. Klikněte na **Next** (Další).  
  
3. Měli byste vidět stromové zobrazení vlastních funkcí. Otevřete **Common Tools**. Měli byste vidět **Visual Studio Extensibility Tools** .  
  
     ![VSSDKInstall](../extensibility/media/vssdkinstall.png "VSSDKInstall")  
  
4. Zaškrtněte **Visual Studio Extensibility Tools** , klikněte na tlačítko **Další** a pokračujte v instalaci.  
  
## <a name="installing-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalace sady Visual Studio SDK po instalaci sady Visual Studio  
 Pokud se rozhodnete nainstalovat sadu Visual Studio SDK po dokončení instalace sady Visual Studio, měli byste postupovat podle následujícího postupu:  
  
1. Otevřete **Ovládací panely/programy/programy a funkce**a vyhledejte **Visual Studio 2015**. Sadu Visual Studio SDK můžete nainstalovat pro všechny edice sady Visual Studio 2015 s výjimkou expresního.  
  
2. Klikněte pravým tlačítkem na **Visual Studio 2015**a pak klikněte na **změnit**. Měla by se zobrazit stránka instalace.  
  
3. Postupujte stejným způsobem jako v **části instalace sady Visual Studio SDK jako součást instalace sady Visual Studio** výše.  
  
4. Kliknutím na odkaz **Visual Studio Extensibility Tools** nainstalujete sadu Visual Studio SDK.  
  
## <a name="installing-the-visual-studio-sdk-from-a-solution"></a>Instalace sady Visual Studio SDK z řešení  
 Pokud otevřete řešení s projektem rozšiřitelnosti bez první instalace VSSDK, zobrazí se vám na zvýrazněný informační panel nad Průzkumník řešení. Měl by vypadat nějak takto:  
  
 ![SolutionExplorerInstall](../extensibility/media/solutionexplorerinstall.png "SolutionExplorerInstall")  
  
## <a name="installing-the-visual-studio-sdk-from-the-command-line"></a>Instalace sady Visual Studio SDK z příkazového řádku  
 VSSDK můžete nainstalovat z příkazového řádku pomocí přepínače **/InstallSelectableItems** s instalačním programem sady Visual Studio. Podrobnosti o použití parametrů příkazového řádku s instalačním programem najdete v tématu [instalace sady Visual Studio 2015](../install/install-visual-studio-2015.md).  
  
 Tady je postup bezobslužné instalace VSSDK pomocí instalačního programu komunity sady Visual Studio 2015:  
  
```  
vs_community.exe /s /installSelectableItems VS_SDK_GROUPV1  
```  
  
 Všimněte si, že je nutné použít instalační program sady Visual Studio, který odpovídá nainstalované verzi sady Visual Studio. Například pokud máte v počítači nainstalovanou Visual Studio Enterprise, musíte spustit instalační program Visual Studio Enterprise (vs_enterprise.exe).
