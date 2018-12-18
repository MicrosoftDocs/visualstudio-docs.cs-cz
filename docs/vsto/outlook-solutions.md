---
title: řešení pro aplikaci Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d0a79d48b8ff054e4c7bdb9151f3eefbf287b24
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831234"
---
# <a name="outlook-solutions"></a>řešení pro aplikaci Outlook
  Visual Studio poskytuje šablony projektu, které slouží k vytváření doplňků VSTO pro aplikaci Microsoft Office Outlook. Doplňky VSTO slouží k automatizaci aplikace Outlook, rozšířit funkce aplikace Outlook nebo přizpůsobení uživatelského rozhraní (UI) aplikace Outlook. Další informace o doplňcích VSTO najdete v tématu [doplňků VSTO architektura](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
## <a name="create-an-outlook-vsto-add-in-project"></a>Vytvoření projektu doplňku aplikace Outlook VSTO  
 S vytvořením projektech Outlook **doplňku aplikace Outlook** šablonu projektu v **nový projekt** dialogové okno. Tato šablona obsahuje odkazy na požadovaná sestavení a soubory projektu.  
  
 Další informace o tom, jak vytvořit projekt doplňku VSTO v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Další informace o šablonách projektů, naleznete v tématu [Přehled šablon projektů Office project](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Aplikace Outlook doplňku VSTO programovací model  
 Při vytváření projektu doplňku VSTO pro Outlook, Visual Studio vygeneruje třídy, nazvané `ThisAddIn`, které jsou základem vašeho řešení. Tato třída poskytuje výchozí bod pro psaní kódu a také poskytuje objektový model aplikace Outlook k doplňku VSTO.  
  
 Další informace o `ThisAddIn` třídy a další funkce můžete použít v VSTO Add-in, naleznete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatizace aplikace Outlook s použitím modelu objektů aplikace Outlook  
 Objektový model aplikace Outlook poskytuje mnoho typů, které můžete použít k automatizaci aplikace Outlook. Tyto typy umožňují také napsat kód k provedení běžných úloh:  
  
- Prostřednictvím kódu programu vytvořit a odeslat e-mailové zprávy.  
  
- Odeslání nových žádostí o schůzku.  
  
- Hledat položky do složky aplikace Outlook.  
  
  Další informace najdete v tématu [přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md).  
  
## <a name="customize-the-user-interface-of-an-outlook-application"></a>Přizpůsobení uživatelského rozhraní aplikace Outlook  
  
|Úloha|Další informace|  
|----------|--------------------------|  
|Přidáte vlastní karty na pás karet je kontrola aplikace Outlook.|[Přehled pásu karet](../vsto/ribbon-overview.md)|  
|Přidáte vlastní skupiny k předdefinované kartě v aplikaci Outlook inspektor.|[Postupy: Přizpůsobení předdefinované karty](../vsto/how-to-customize-a-built-in-tab.md)|  
|Přidání vlastního podokna úloh, které se zobrazí v je kontrola aplikace Outlook|[Vlastní podokna úloh](../vsto/custom-task-panes.md).|  
|Přidání oblasti formuláře, který rozšiřuje nebo nahradí existující formulářů aplikace Outlook.|[Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Další informace o přizpůsobení uživatelského rozhraní aplikace Outlook a další aplikace Microsoft Office, naleznete v tématu [přizpůsobení uživatelského rozhraní Office](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)|Poskytuje přehled o objekty, které jsou k dispozici v modelu objektů aplikace Outlook.|  
|[Vytváření oblastí formulářů aplikace Outlook](../vsto/creating-outlook-form-regions.md)|Popisuje nástroje poskytovaný sadou Visual Studio, které usnadňují návrh, vývoj a ladění oblasti formuláře.|  
|[Návod: Vytvoření vašeho prvního doplňku VSTO pro Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Ukazuje, jak vytvoření doplňku VSTO pro aplikaci Microsoft Office Outlook.|  
|[Outlook 2010 ve vývoji Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Oblasti v knihovně MSDN, kde můžete vyhledat články a referenční dokumentaci o vývoji řešení pro aplikaci Outlook (nezávislé na vývoj pro Office pomocí sady Visual Studio).|  
  
  