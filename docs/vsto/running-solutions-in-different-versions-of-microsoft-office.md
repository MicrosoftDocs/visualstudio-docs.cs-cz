---
title: Spouštění řešení v různých verzích systému Microsoft Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ed8a9b7cc78b0605b7fcc3931a7ee8992360125b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675724"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Spouštění řešení v různých verzích systému Microsoft Office
    
## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Spuštění řešení pro Office vytvořená pomocí sady Visual Studio 2010 a vyšší  
  
|Verze systému Office cílí šablony projektu|Cílit na rozhraní .NET Framework projektu<sup>1</sup>|Verze systému Office, který umožňuje spouštět řešení|Požadované modulu runtime v počítači koncového uživatele|  
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|  
|Office 2016 a [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Systém Microsoft Office 2007<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Systém Microsoft Office 2007<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|  
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|  
|2007 – systém Microsoft Office|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější,<br /><br /> or<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 – systém Microsoft Office|Visual Studio 2010 Tools for Office Runtime|  
  
 1. Verze rozhraní .NET Framework, které vyžaduje váš projekt cílí na počítačích koncových uživatelů pro spuštění řešení. Například pokud váš projekt cílí na rozhraní .NET Framework 3.5, je požadováno rozhraní .NET Framework 3.5 v počítačích koncových uživatelů. V tomto příkladu řešení nespustí, pokud je to jenom [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] je nainstalovaný na počítačích koncových uživatelů.  
  
 2. V tomto scénáři řešení se spustí bez chyb v systému Microsoft Office 2007 pouze v případě, že ho nepoužívá funkce, které jsou nové v [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Spuštění řešení pro Office vytvořená pomocí verze sady Visual Studio před Visual Studio 2010  
 Aplikace Microsoft Office může spustit řešení vytvořená pomocí verze sady Visual Studio před Visual Studio 2010. V některých případech tato řešení vyžadují různé verze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Různé verze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] lze nainstalovat souběžně na stejném počítači.  
  
 Následující tabulka uvádí, které verze systému Microsoft Office může spustit řešení vytvořená pomocí předchozí verze sady Visual Studio a které verze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] a rozhraní .NET Framework jsou požadovány pro každé řešení.  
  
|Edice sady Visual Studio používá k vytvoření řešení|Verze systému Office cílí šablony projektu|Verze systému Office, který umožňuje spouštět řešení|Požadované modulu runtime v počítači koncového uživatele|Požadovaná verze rozhraní .NET Framework v počítači koncového uživatele|  
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|  
|Visual Studio 2008 Professional<br /><br /> or<br /><br /> Visual Studio Team System 2008|2007 – systém Microsoft Office|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> 2007 – systém Microsoft Office|Visual Studio 2010 Tools for Office Runtime<sup>1</sup><br /><br /> or<br /><br /> Visual Studio Tools pro systém Microsoft Office (verze 3.0 Runtime)|.NET Framework 3.5|  
|Jeden z následujících edicí sady Visual Studio 2005 s VSTO 2005 SE<sup>2</sup> nainstalovaný:<br /><br /> – Visual Studio 2005 Tools for Office<br />– Visual Studio Team System 2005<br />– Visual Studio 2005 Professional|2007 – systém Microsoft Office|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32bitová verze pouze<sup>3</sup>)<br /><br /> 2007 – systém Microsoft Office|Visual Studio 2005 Tools for Office Druhé vydání modulu Runtime|Rozhraní .NET framework 2.0, rozhraní .NET Framework 3.0 nebo .NET Framework 3.5|  
|Některé z následujících edicí sady Visual Studio:<br /><br /> – Visual Studio 2008 Professional<br />– Visual Studio Team System 2008<br />– Visual Studio 2005 Tools for Office (s nebo bez něj VSTO 2005 SE<sup>2</sup> nainstalovaná)<br />– Visual Studio Team System 2005 (s nebo bez něj VSTO 2005 SE<sup>2</sup> nainstalovaná)<br />– 2005 visual Studio Professional with VSTO 2005 SE<sup>2</sup> nainstalovaná|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32bitová verze pouze<sup>3</sup>)<br /><br /> 2007 – systém Microsoft Office<br /><br /> Microsoft Office 2003|Visual Studio 2005 Tools for Office Druhé vydání modulu Runtime|Rozhraní .NET framework 2.0, rozhraní .NET Framework 3.0 nebo .NET Framework 3.5|  
  
 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikace zahrnují Visual Studio 2010 Tools for Office runtime. Proto tyto aplikace vždycky používat Visual Studio 2010 Tools for Office runtime spíše než Visual Studio Tools pro systém Microsoft Office (verze 3.0 Runtime) v tomto scénáři. Aplikace v systému Microsoft Office 2007, můžete použít Visual Studio 2010 Tools pro systém Office Runtime nebo Visual Studio Tools pro Microsoft Office system (verze 3.0 Runtime).  
  
 2. VSTO 2005 SE je bezplatný doplněk sady Visual Studio, který obsahuje šablony projektů doplňků VSTO pro Microsoft Office 2003 a systému Microsoft Office 2007. Nainstalujete ho pomocí sady Visual Studio 2005 Professional, Visual Studio 2005 Tools for Office nebo edice sady Visual Studio Team System 2005. Další informace najdete v tématu [Visual Studio 2005 Tools for Office Druhé vydání](http://go.microsoft.com/fwlink/?LinkId=148446).  
  
 3. Řešení pro systém Office, které vyžadují Visual Studio 2005 Tools for Office Second Edition Runtime nejsou kompatibilní s 64bitovými verzemi [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Ke spouštění těchto řešení v 64bitové verzi [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] nebo [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], musíte upgradovat projekt tak, aby [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] nebo do projektu sady Visual Studio 2008, který cílí na systém Microsoft Office 2007.  
  
## <a name="see-also"></a>Viz také:  
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Visual Studio Tools for Office runtime – přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Visual Studio Tools for Office runtime instalace scénáře](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)  
  
  