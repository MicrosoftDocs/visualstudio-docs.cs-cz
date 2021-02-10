---
title: Vytváření stránek aplikace pro SharePoint | Microsoft Docs
description: Vytvořte stránky aplikace pro službu SharePoint. Stránka aplikace je webová stránka ASP.NET, která je navržena pro použití na webu služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9ecd6573573d76c3e47a2c87a4f455cb9890fb31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949178"
---
# <a name="create-application-pages-for-sharepoint"></a>Vytváření stránek aplikací pro službu SharePoint
  *Stránka aplikace* je webová stránka ASP.NET, která je navržena pro použití na webu služby SharePoint. Stránky aplikace jsou specializovaného typu stránky ASP.NET. Hlavním rozdílem mezi stránkou aplikace a standardní stránkou ASP.NET je, že stránka aplikace obsahuje obsah, který je sloučen se stránkou předlohy služby SharePoint. Stránka předlohy umožňuje stránkám aplikace sdílet stejný vzhled a chování jako ostatní stránky na webu.

 Visual Studio umožňuje navrhovat stránky aplikací pomocí návrháře. Návrhář zobrazí oblast obsahu pro každý zástupný text obsahu, který je definován na stránce předlohy. Stránku aplikace lze navrhnout přetažením ovládacích prvků do těchto oblastí obsahu.

## <a name="application-pages"></a>Stránky aplikace
 Stránky aplikace jsou sdíleny ve všech webech na serveru, zatímco stránka lokality je specifická pro jednu lokalitu. Další informace, [typy stránek služby SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

 Ve výchozím nastavení se většina stránek, které se zobrazí při vytváření webu služby SharePoint, nachází na stránkách webu. Stránku webu lze přidat do knihovny stránek služby SharePoint. Uživatelé mohou přizpůsobit stránku webu pomocí nástrojů, jako je například SharePoint Designer. Stránka webu může také hostovat funkce, jako jsou dynamické Webové části a zóny webových částí.

 Stránky aplikace nemůžou dělat tyto věci. Stránka aplikace je ale nejlepší typ stránky, která se má vytvořit, pokud chcete, aby stránka obsahovala vlastní kód. I když můžete přidat vlastní kód na stránku webu, kód se zastaví, když uživatel stránku přizpůsobí pomocí nástrojů, jako je SharePoint Designer.

> [!NOTE]
> Visual Studio neposkytuje šablony, které vám pomůžou vytvářet stránky webu pro SharePointový Web. Další informace naleznete v tématu [typy stránek služby SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

## <a name="create-an-application-page"></a>Vytvoření stránky aplikace
 Chcete-li vytvořit stránku aplikace, přidejte položku **stránky aplikace** do projektu služby SharePoint. Když vytvoříte stránku aplikace, Visual Studio přidá do projektu následující složky:

|Složka|Description|
|------------|-----------------|
|Rozložení|Mapuje se na _layouts virtuální adresář systému souborů SharePoint.|
|Podsložka rozložení|Obsahuje soubory, které tvoří stránku aplikace. Ve výchozím nastavení má tato složka stejný název jako projekt. Tuto složku můžete kdykoli přejmenovat. Při spuštění projektu aplikace Visual Studio nasadí tuto složku do _layouts virtuálního adresáře systému souborů SharePoint.|

 Visual Studio přidá do projektu následující soubory:

|Soubor|Description|
|----------|-----------------|
|Stránkovací soubor ASP.NET (*. aspx*)|Obsahuje kód XML, který definuje stránku.|
|Soubor kódu stránky aplikace|Obsahuje kód za stránkou aplikace. Přidejte kód, který zpracovává události do tohoto souboru.|
|Soubor s kódem návrháře stránky aplikace|Obsahuje kód, který je generován návrhářem. Neupravujte přímo tento soubor.|

## <a name="design-and-debug-an-application-page"></a>Návrh a ladění stránky aplikace
 Navrhněte obsah stránky aplikace pomocí zobrazení návrháře v aplikaci Visual Studio. Tento návrhář se zobrazí, když otevřete stránku aplikace ve vašem projektu (dvojitým kliknutím na něj nebo otevřením jeho místní nabídky a následným výběrem možnosti **otevřít**) a kliknutím na tlačítko **Návrh** v dolní části editoru.

> [!NOTE]
> Stránku lze navrhnout pouze v zobrazení **zdroj** v návrháři. **Návrhové** zobrazení návrháře je pro stránky aplikací zakázané.

 Můžete ladit stránku aplikace stejně, jako byste ladit jiné položky projektu služby SharePoint v aplikaci Visual Studio. Když spustíte ladicí program sady Visual Studio, Visual Studio otevře web služby SharePoint.

 Chcete-li zobrazit stránku aplikace, je nutné ručně přejít do umístění stránky aplikace (například: http://<em>server_name</em>/_layouts/*PROJECT_NAME*/ApplicationPage1.aspx).

 Další informace o tom, jak ladit projekty služby SharePoint, naleznete v tématu [řešení potíží s řešeními služby SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Výběr stránky předlohy
 Ve výchozím nastavení položka **stránky aplikace** odkazuje na stránku předlohy webu, kterou používáte k ladění projektu. Tato stránka má název v4. Master a najdete ji v **galerii stránek předlohy** webu služby SharePoint.

 Můžete explicitně změnit, která hlavní stránka je používána stránkou aplikace, nastavením `MasterPageFile` atributu `Page` elementu Application. (Například: `MasterPageFile="~/_layouts/applicationv4.master"` ). Ve skutečnosti je nutné nastavit tento atribut, pokud nejsou na serveru SharePoint povoleny dynamické stránky předlohy. Další informace o stránkách předlohy v SharePointu najdete v tématu [stránky předlohy](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14)).

## <a name="see-also"></a>Viz také
- [Vývoj pro SharePoint Foundation v Hloubkě](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [Přehled ASP.NET](/aspnet/overview)
- [ASP.NET – webové stránky](/aspnet/web-pages/index)
