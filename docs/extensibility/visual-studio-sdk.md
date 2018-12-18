---
title: Visual Studio SDK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5701044e20f2122199d9d0ca5558e453e6e5f72
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906023"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK umožňuje rozšířit funkce aplikace Visual Studio nebo systém integrovat nové funkce do sady Visual Studio. Můžete distribuovat rozšíření ostatním uživatelům, tak na Visual Studio Marketplace. Tady jsou některé způsoby, ve kterém můžete rozšíření sady Visual Studio:  
  
- Přidání příkazů, tlačítek, nabídek a další prvky uživatelského rozhraní do integrovaného vývojového prostředí  
  
- Přidat nové funkce okna nástrojů  
  
- Rozšíření technologie IntelliSense pro daný jazyk, nebo na poskytovat technologii IntelliSense pro nový programovací jazyky  
  
- Ikony žárovky používat k poskytování pomocné parametry a návrhy, které pomáhá vývojářům psát lepší kód  
  
- Povolit podporu pro nový jazyk  
  
- Přidat do vlastního typu projektu  
  
- Oslovení miliónů vývojářů prostřednictvím Visual Studio Marketplace  
  
  Pokud jste nikdy napsali před rozšíření sady Visual Studio, byste měli najít další informace o těchto funkcích a na [Začínáme s vývojem rozšíření sady Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="install-the-visual-studio-sdk"></a>Instalace sady Visual Studio SDK  
 Visual Studio SDK je volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Co je nového ve Visual Studio 2017 SDK  
 Visual Studio SDK má několik nových funkcí, jako je formát VSIX v3, jakož i rozbíjející změny, které by mohly vyžadovat aktualizace rozšíření. Další informace najdete v tématu [co je nového ve Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio zkušenosti uživatelů  
 Skvělé tipy k návrhu uživatelského rozhraní pro rozšíření v [zkušenosti uživatelů sady Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Můžete také zjistíte, jak vypadají skvěle na vysoké rozlišení DPI zařízení pomocí rozšíření [vydává adresu DPI](../extensibility/addressing-dpi-issues2.md) článku.  
  
 Využijte výhod [Image service a katalog](../extensibility/image-service-and-catalog.md) Správa skvělé imagí a podpora vysokého nastavení DPI a motivů.  
  
## <a name="find-and-install-existing-visual-studio-extensions"></a>Najít a nainstalovat rozšíření existující sady Visual Studio  
 S rozšířeními Visual Studia můžete najít **rozšíření a aktualizace** dialogového okna na **nástroje** nabídky. Další informace najdete v tématu [hledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Rozšíření můžete také vyhledat [Visual Studio marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Referenční dokumentace jazyka Visual Studio SDK  
 Můžete najít referenční dokumentace rozhraní API sady Visual Studio SDK na [referenční dokumentace jazyka Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Ukázky sady Visual Studio SDK  
 Můžete najít příklady opensourcové rozšíření VS SDK na Githubu v [ukázky sady Visual Studio](https://aka.ms/vs2015sdksamples). Úložiště GitHub obsahuje ukázky, které ukazují různé rozšiřitelné funkce v sadě Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Další prostředky sady Visual Studio SDK  
 Pokud máte dotazy týkající VSSDK nebo chcete sdílet vaše prostředí pro vývoj rozšíření, můžete použít [Visual Studio Extensibility fórum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) nebo [ExtendVS Gitteru Chatroom](https://gitter.im/Microsoft/extendvs).  
  
 Můžete najít další informace najdete v [VSX Arcana blogu](https://blogs.msdn.microsoft.com/vsx/) a počet blogy autorem MVPs společnosti Microsoft:  
  
-   [Oblíbená rozšíření sady Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Rozšíření produktu Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Rozšíření sady Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Viz také:  
 [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Postupy: migrace projektů rozšíření do sady Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Nejčastější dotazy: Převádění doplňků na rozšíření VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Správa více vláken ve spravovaném kódu](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)   
 [Přidání příkazů na panely nástrojů](../extensibility/adding-commands-to-toolbars.md)   
 [Rozšíření a přizpůsobení nástrojů systému windows](../extensibility/extending-and-customizing-tool-windows.md)   
 [Jazyk a Editor rozšíření služeb](../extensibility/editor-and-language-service-extensions.md)   
 [Rozšíření projektů](../extensibility/extending-projects.md)   
 [Rozšířit možnosti a nastavení uživatele](../extensibility/extending-user-settings-and-options.md)   
 [Vytváření vlastních šablon projektů a položek](../extensibility/creating-custom-project-and-item-templates.md)   
 [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md)   
 [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)   
 [Správa rozšíření VSPackages](../extensibility/managing-vspackages.md)   
 [Prostředí sady Visual Studio izolovaný režim](../extensibility/visual-studio-isolated-shell.md)   
 [Dodávejte rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [V sadě Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Podpora pro sadu Visual Studio SDK](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archiv](../extensibility/archive.md)   
 [Referenční dokumentace jazyka Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
