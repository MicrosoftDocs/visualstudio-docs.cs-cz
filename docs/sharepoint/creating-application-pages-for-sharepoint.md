---
title: Vytváření stránek aplikací pro SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f1c3b03507ca97724106c6ca1d121b3c54eb659
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853139"
---
# <a name="create-application-pages-for-sharepoint"></a>Vytváření stránek aplikací pro SharePoint
  *Stránky aplikace* je webová stránka ASP.NET, který je určený k použití na webu služby SharePoint. Stránky aplikací jsou speciální typ stránky ASP.NET. Hlavní rozdíl mezi stránku aplikace a standardní stránky technologie ASP.NET je, že stránky aplikace obsahuje obsah, který je sloučen s hlavní stránkou služby SharePoint. Hlavní stránky umožňuje, aby aplikace stránky, které sdílejí stejný vzhled a chování jako další stránky na webu.  
  
 Visual Studio umožňuje návrh stránek aplikací pomocí návrháře. Návrhář zobrazí oblasti obsahu pro každou zástupný symbol obsahu, který je definován na hlavní stránce. Stránka aplikace můžete navrhnout přetažením ovládacích prvků na tyto oblasti obsahu.  
  
## <a name="application-pages"></a>Stránky aplikací
 Stránky aplikace se sdílí na všech webech na serveru, zatímco stránky webu je specifická pro jednu lokalitu. Další informace najdete [typů stránku služby SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
 Většina těchto stránek, které se zobrazí při vytváření webu služby SharePoint jsou ve výchozím nastavení stránky webu. Stránka webu je přidat do knihovny SharePoint stránky. Uživatelé mohou přizpůsobit stránky webu pomocí nástrojů, jako je SharePoint designeru. Stránka webu mohli hostovat i funkce, jako je dynamické webové části a zóny webové části.  
  
 Stránky aplikací nemůžete provádět tyto akce. Stránky aplikace je ale nejlepší typ stránky pro vytvoření, pokud chcete, aby stránka obsahuje vlastní kód. I když přidáte vlastní kód na stránku webu, kód zastaví spuštění, když uživatel přizpůsobuje stránky s využitím nástrojů, jako je SharePoint designeru.  
  
> [!NOTE]  
>  Visual Studio neposkytuje šablony, které vám pomůžou vytvořit stránky webu pro web služby SharePoint. Další informace najdete v tématu [typů stránku služby SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).  
  
## <a name="create-an-application-page"></a>Vytvoření stránky aplikace
 Chcete-li vytvořit stránku aplikace, přidejte **stránky aplikace** položky projektu služby SharePoint. Při vytváření stránky aplikace Visual Studio přidá následující složky do projektu:  
  
|Folder|Popis|  
|------------|-----------------|  
|Rozložení|Mapuje se na virtuální adresář _layouts systému souborů služby SharePoint.|  
|Rozložení podsložky|Obsahuje soubory, které tvoří stránky aplikace. Ve výchozím nastavení tato složka obsahuje stejný název jako projekt. Kdykoli můžete přejmenovat tuto složku. Při spuštění projektu sady Visual Studio nasadí tato složka na virtuální adresář _layouts systému souborů služby SharePoint.|  
  
 Visual Studio přidá následující soubory do projektu:  
  
|Soubor|Popis|  
|----------|-----------------|  
|Soubor stránky technologie ASP.NET (*.aspx*)|Obsahuje kód XML, který definuje stránky.|  
|Soubor kódu stránky aplikace|Obsahuje kódu stránky aplikace. Přidejte kód, který zpracovává události do tohoto souboru.|  
|Soubor návrháře kódu stránky aplikace|Obsahuje kód, který je generovaný návrhářem. Neupravujte přímo tohoto souboru.|  
  
## <a name="design-and-debug-an-application-page"></a>Návrh a ladění stránky aplikace
 Návrh obsah stránky aplikace pomocí návrháře zobrazení v sadě Visual Studio. Tento návrhář zobrazí při otevření stránky aplikace ve vašem projektu (poklepáním nebo otevřením jeho místní nabídku a následným výběrem možnosti **otevřete**) a klikněte na tlačítko **návrhu** tlačítko v dolní části editor.  
  
> [!NOTE]  
>  Na stránce můžete navrhnout pouze v **zdroj** zobrazení návrháře. **Návrhu** zobrazení návrháře je zakázaná pro stránky aplikace.  
  
 Stránky aplikace můžete ladit stejně, jako by ladění ostatních položek projektu služby SharePoint v sadě Visual Studio. Při spuštění ladicího programu sady Visual Studio, Visual Studio otevře web služby SharePoint.  
  
 Pokud chcete zobrazit stránku aplikace, je nutné ručně přejít na umístění aplikace na stránce (například: http://<em>název_serveru</em>adresáři /_layouts/*Project_Name*/ApplicationPage1.aspx).  
  
 Další informace o tom, jak ladění projektů SharePoint naleznete v tématu [řešení potíží s SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="choose-a-master-page"></a>Vyberte stránku předlohy
 Ve výchozím nastavení **stránky aplikace** položka odkazuje na hlavní stránku webu, který používáte k ladění projektu. Že stránka s názvem v4.master a najdete ho podle **Galerie stránky předlohy** webu služby SharePoint.  
  
 Můžete explicitně změnit na stránce, které hlavní stránky aplikace používá tak, že nastavíte `MasterPageFile` atribut aplikace `Page` elementu. (Příklad: `MasterPageFile="~/_layouts/applicationv4.master"`). Ve skutečnosti je nutné nastavit tento atribut, pokud na serveru SharePoint nejsou povoleny dynamické stránky předlohy. Další informace o stránkách předlohy služby SharePoint, naleznete v tématu [stránky předlohy](http://go.microsoft.com/fwlink/?LinkID=169281).  
  
## <a name="see-also"></a>Viz také:
 [Vývoj pro SharePoint Foundation do hloubky](http://go.microsoft.com/fwlink/?LinkID=182103)   
 [ASP.NET: Přehled](/aspnet/overview)   
 [Webové stránky ASP.NET](/aspnet/web-pages/index)   
  
