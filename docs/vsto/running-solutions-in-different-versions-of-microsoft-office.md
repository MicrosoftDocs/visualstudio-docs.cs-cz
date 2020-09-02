---
title: Spouštění řešení v různých verzích systém Microsoft Office
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 15d0a3611f314abe4b571f2235346dde55d6e358
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985601"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Spouštění řešení v různých verzích systém Microsoft Office

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Spouštění řešení pro Office vytvořených pomocí sady Visual Studio 2010 a vyšší

|Verze Office cílené šablonou projektu|Cílová .NET Framework projektu<sup>1</sup>|Verze Office, které můžou řešení spustit|Požadovaný modul runtime na počítači koncového uživatele|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Office 2016 a [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 systém Microsoft Office systém<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 systém Microsoft Office systém<sup>2</sup>|Visual Studio 2010 Tools for Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools for Office Runtime|
|2007 – systém Microsoft Office|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější,<br /><br /> nebo<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 – systém Microsoft Office|Visual Studio 2010 Tools for Office Runtime|

 1. Verze .NET Framework, na kterou váš projekt cílí, je požadována na počítačích koncových uživatelů, aby vaše řešení běželo. Například pokud váš projekt cílí na .NET Framework 3,5, je .NET Framework 3,5 nutné na počítačích koncových uživatelů. V tomto příkladu se vaše řešení nespustí, pokud [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] se na počítačích koncových uživatelů nainstaluje jenom.

 2. V tomto scénáři se řešení spustí bez chyb v systému 2007 systém Microsoft Office pouze v případě, že nepoužívá funkce, které jsou v nástroji novinkou [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Spuštění řešení pro systém Office vytvořeného pomocí verzí sady Visual Studio před sadou Visual Studio 2010
 Aplikace systém Microsoft Office mohou spouštět řešení vytvořená pomocí verzí sady Visual Studio před Visual Studio 2010. V některých případech tato řešení vyžadují různé verze nástroje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Různé verze nástroje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] lze nainstalovat vedle sebe na stejný počítač.

 Následující tabulka uvádí, které verze systém Microsoft Office mohou spouštět řešení vytvořená pomocí předchozích verzí sady Visual Studio a které verze [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] a .NET Framework jsou požadovány pro každé řešení.

|Edice Visual studia, která se používá k vytvoření řešení|Verze Office cílené šablonou projektu|Verze Office, které můžou řešení spustit|Požadovaný modul runtime na počítači koncového uživatele|Požadovaná verze .NET Framework na počítači koncového uživatele|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> nebo<br /><br /> Visual Studio Team System 2008|2007 – systém Microsoft Office|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] <sup>1</sup><br /><br /> 2007 – systém Microsoft Office|Visual Studio 2010 Tools pro Office runtime<sup>1</sup><br /><br /> nebo<br /><br /> Visual Studio Tools pro systém Microsoft Office systém (verze 3,0 Runtime)|.NET Framework 3.5|
|Jedna z následujících edicí sady Visual Studio 2005 s nainstalovanou službou VSTO 2005 SE<sup>2</sup> :<br /><br /> – Visual Studio 2005 Tools pro Office<br />– Visual Studio Team System 2005<br />– Visual Studio 2005 Professional|2007 – systém Microsoft Office|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32 – pouze bitů<sup>3</sup>)<br /><br /> 2007 – systém Microsoft Office|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2,0, .NET Framework 3,0 nebo .NET Framework 3,5|
|Kterákoli z následujících edicí sady Visual Studio:<br /><br /> – Visual Studio 2008 Professional<br />– Visual Studio Team System 2008<br />– Visual Studio 2005 Tools for Office (s nainstalovanou sadou VSTO 2005 se<sup>2</sup> nebo bez ní)<br />– Visual Studio Team System 2005 (s nainstalovanou sadou VSTO 2005 se<sup>2</sup> nebo bez ní)<br />– Visual Studio 2005 Professional with VSTO 2005 SE<sup>2</sup> nainstalovalo|systém Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (32 – pouze bitů<sup>3</sup>)<br /><br /> 2007 – systém Microsoft Office<br /><br /> systém Microsoft Office 2003|Visual Studio 2005 Tools for Office Second Edition Runtime|.NET Framework 2,0, .NET Framework 3,0 nebo .NET Framework 3,5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)][!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]aplikace a zahrnují sady Visual Studio 2010 Tools for Office runtime. Proto tyto aplikace vždy používají sadu Visual Studio 2010 Tools for Office runtime místo Visual Studio Tools pro systém Microsoft Office systém (verze 3,0 Runtime) v tomto scénáři. Aplikace v systému 2007 systém Microsoft Office můžou používat Visual Studio 2010 Tools for Office runtime nebo Visual Studio Tools pro systém Microsoft Office systém (verze 3,0 Runtime).

 2. VSTO 2005 SE nejedná o bezplatný doplněk sady Visual Studio, který poskytuje šablony projektů doplňku VSTO pro systém Microsoft Office 2003 a systém 2007 systém Microsoft Office. Dá se nainstalovat pomocí sady Visual Studio 2005 Professional, Visual Studio 2005 Tools for Office nebo edice v sadě Visual Studio Team System 2005. Další informace naleznete v tématu [Visual Studio 2005 Tools for Office Second Edition](https://developer.microsoft.com/office/docs).

 3. Řešení Office, která vyžadují Visual Studio 2005 Tools for Office Second Edition Runtime, nejsou kompatibilní s verzemi 64 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] . Chcete-li spustit Tato řešení v 64-bit Edition systému [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] nebo [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] , je nutné upgradovat projekt na [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] projekt sady Visual Studio 2008, který se zaměřuje na 2007 systém Microsoft Office systém.

## <a name="see-also"></a>Viz také
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Přehled prostředí Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Scénáře instalace Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
