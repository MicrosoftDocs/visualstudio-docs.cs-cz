---
title: Visual Studio SDK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e64506ca544dd3811864358f9c928f6893dc8448
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758976"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio SDK umožňuje rozšířit funkce aplikace Visual Studio nebo systém integrovat nové funkce do sady Visual Studio. Rozšíření ostatním uživatelům, a také do Galerie Visual Studio můžete distribuovat. Tady jsou některé způsoby, ve kterém můžete rozšíření sady Visual Studio:  
  
- Přidání příkazů, tlačítek, nabídek a další prvky uživatelského rozhraní do integrovaného vývojového prostředí  
  
- Přidat nové funkce okna nástrojů  
  
- Rozšíření technologie IntelliSense pro daný jazyk, nebo na poskytovat technologii IntelliSense pro nový programovací jazyky  
  
- Ikony žárovky používat k poskytování pomocné parametry a návrhy, které pomáhá vývojářům psát lepší kód  
  
- Povolit podporu pro nový jazyk  
  
- Přidat do vlastního typu projektu  
  
- Oslovení miliónů vývojářů prostřednictvím Galerie sady Visual Studio  
  
  Pokud jste nikdy napsali před rozšíření sady Visual Studio, byste měli najít další informace o těchto funkcích a na [spuštění pro vývoj rozšíření sady Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalace sady Visual Studio SDK  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Co je nového ve Visual Studio 2015 SDK  
 Visual Studio SDK má několik nových funkcí, včetně návrhy a nové položky projektu, které vám umožňují vytvářet příkazy nabídky, panely nástrojů a rozšíření editoru pomocí balíčku VSIX. Další informace najdete v tématu [co je nového ve službě Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Pravidla pro práci s uživatelským prostředím sady Visual Studio  
 Skvělé tipy k návrhu uživatelského rozhraní pro rozšíření v [Visual Studio zkušenosti uživatelů](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Můžete také zjistíte, jak se vaše rozšíření, které vypadají skvěle na vysoké rozlišení DPI zařízení s naší [řešení problémů s nastavením DPI](../extensibility/addressing-dpi-issues2.md) tématu.  
  
 Využijte výhod [služba bitových kopií a katalog](../extensibility/image-service-and-catalog.md) Správa skvělé imagí a podpora vysokého nastavení DPI a motivů.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Vyhledání a instalace rozšíření existující sady Visual Studio  
 S rozšířeními Visual Studia můžete najít **rozšíření a aktualizace** dialogového okna na **nástroje** nabídky. Další informace najdete v tématu [hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Rozšíření můžete také vyhledat [Galerie sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Referenční dokumentace sady Visual Studio SDK  
 Můžete najít referenční dokumentace rozhraní API sady Visual Studio SDK na [referenční dokumentace jazyka Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Ukázky sady Visual Studio SDK  
 Můžete najít příklady opensourcové rozšíření VS SDK na Githubu v [ukázky sady Visual Studio](https://aka.ms/vs2015sdksamples). Úložiště GitHub obsahuje ukázky, které ukazují různé rozšiřitelné funkce v sadě Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Další materiály pro Visual Studio SDK  
 Pokud máte dotazy týkající VSSDK nebo chcete sdílet vaše prostředí pro vývoj rozšíření, můžete použít [Visual Studio Extensibility fórum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) nebo [konverzace skupiny ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Můžete najít další informace najdete v [VSX Arcana blogu](http://blogs.msdn.com/b/vsx/) a počet blogy autorem MVPs společnosti Microsoft:  
  
-   [Rozšíření Oblíbené aplikace Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Rozšiřitelnost sady Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Rozšíření sady Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Viz také  
 [Vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Postupy: migrace projektů rozšíření do sady Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Nejčastější dotazy: Převádění doplňků na rozšíření VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Správa více vláken ve spravovaném kódu](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)   
 [Přidání příkazů na panely nástrojů](../extensibility/adding-commands-to-toolbars.md)   
 [Rozšíření a přizpůsobení nástrojů Windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor a rozšíření služeb jazyka](../extensibility/editor-and-language-service-extensions.md)   
 [Rozšíření projektů](../extensibility/extending-projects.md)   
 [Rozšíření uživatelských nastavení a možnosti](../extensibility/extending-user-settings-and-options.md)   
 [Vytváření vlastních projektů a šablon položek](../extensibility/creating-custom-project-and-item-templates.md)   
 [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)   
 [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Rozšíření připojené služby](../extensibility/extending-connected-services.md)   
 [Správa rozšíření VSPackages](../extensibility/managing-vspackages.md)   
 [Izolované prostředí sady Visual Studio](../extensibility/visual-studio-isolated-shell.md)   
 [Přesouvání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [V sadě Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Podpora pro sadu Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archiv](../extensibility/archive.md)   
 [Referenční dokumentace sady Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)

