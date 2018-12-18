---
title: InfoPath – řešení
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ae2882cbf38349eac57f1dfb731cc7d717769a4
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670855"
---
# <a name="infopath-solutions"></a>InfoPath – řešení
  Visual Studio poskytuje šablony projektu, které slouží k vytváření doplňků VSTO pro Microsoft Office InfoPath 2013 a Infopathu 2010. InfoPath není k dispozici v Office 2016.  
  
> [!NOTE]  
>  Můžete stále vytvořit doplňku VSTO pro InfoPath i v případě, že jste nainstalovali Office 2016. Stačí nainstalujte aplikace InfoPath 2013 nebo Office 2013-souběžně s Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
 Doplňků VSTO pro InfoPath se podobají doplňků VSTO pro jiné aplikace Microsoft Office. Tyto druhy řešení obsahovat sestavení, který je načten aplikací. Koncoví uživatelé mají přístup k funkcím tohoto sestavení bez ohledu na to, kterou formulář nebo formulář šablony je otevřený. Další informace o doplňcích VSTO najdete v tématu [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md) a [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 nezahrnuje projekty šablony formuláře InfoPath, které byly k dispozici v předchozích verzích sady Visual Studio. Visual Studio 2015 také nelze použít k otevření nebo upravit projekt šablony formuláře InfoPath, který byl vytvořen v předchozí verzi sady Visual Studio. Můžete však otevřít a upravit projekt šablony formuláře InfoPath pomocí Visual Studio Tools for Applications. Další informace najdete v tématu [pracovat s projekty VSTO 2008 v Infopathu 2010.](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## <a name="automate-infopath-by-using-an-add-in"></a>Automatizace aplikace InfoPath s využitím doplňku  
 Chcete-li objektový model aplikace InfoPath přístup z Office doplňku VSTO vytvořené pomocí nástroje pro vývoj pro Office v sadě Visual Studio, použijte `Application` pole `ThisAddIn` třídu ve vašem projektu. `Application` Pole vrátí <xref:Microsoft.Office.Interop.InfoPath.Application> objekt, který představuje aktuální instanci aplikace InfoPath. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Při volání do objektového modelu aplikace InfoPath v doplňku VSTO pomocí typů, které jsou k dispozici ve primárního spolupracujícího sestavení pro aplikaci InfoPath. Primární spolupracující sestavení funguje jako most mezi spravovaného kódu v doplňku VSTO a objekt modelu COM v aplikaci InfoPath. Všechny typy ve primárního spolupracujícího sestavení aplikace InfoPath, které jsou definovány v <xref:Microsoft.Office.Interop.InfoPath> oboru názvů. Další informace o primární spolupracující sestavení aplikace InfoPath, naleznete v tématu [primární sestavení zprostředkovatele komunikace o the Microsoft Office InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Další informace o primárních sestavení vzájemné spolupráce obecné naleznete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) a [primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Přizpůsobení uživatelského rozhraní aplikace InfoPath s využitím doplňku  
 Při vytvoření doplňku VSTO pro InfoPath, máte několik různých možností přizpůsobení uživatelského rozhraní. Následující tabulka uvádí některé z těchto možností.  
  
|Úloha|Další informace|  
|----------|--------------------------|  
|Vytvoření vlastního podokna úloh.|[Vlastní podokna úloh](../vsto/custom-task-panes.md)|  
|Přidáte vlastní karty na pás karet v aplikaci InfoPath.|[Přizpůsobte pás karet pro aplikaci InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Další informace o přizpůsobení uživatelského rozhraní aplikace InfoPath a další aplikace Microsoft Office, naleznete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Viz také:  
 [O primárního spolupracujícího sestavení Microsoft Office InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)   
 [Primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [InfoPath 2010 ve vývoji Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  