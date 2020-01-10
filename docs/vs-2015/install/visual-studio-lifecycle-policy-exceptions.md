---
title: Výjimky zásad životního cyklu sady Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 246ffa914ba21b9b2813abca1bae063162576486
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852147"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Výjimky ze zásad životního cyklu sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio obsahuje sbírku kompilátorů, jazyků, modulů runtime, prostředí a dalších prostředků, které umožňují vývoj pro mnoho platforem Microsoftu. Visual Studio může pro potřeby zákazníků instalovat určité sady SDK a další komponenty společnosti Microsoft, které cílí a podporují tyto platformy Microsoftu. Tyto komponenty mohou být licencovány a podporovány podle vlastních podmínek a zásad.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Externí komponenty, které následují zásady životního cyklu kromě zásad sady Visual Studio  
 Následující tabulka uvádí součásti platformy Microsoft, které mohou být součástí sady Visual Studio (v závislosti na konkrétní edici softwaru sady Visual Studio) a které podléhají vlastním zásadám podpory a časovým rámcům.  
  
|PRODUKTOVÁ ŘADA|EXTERNÍ NÁZEV|  
|--------------------|-------------------|  
|[.NET 3.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|.NET 4.5.1 MT Pack (Classic)<br /><br /> .NET 4.5.1 Multi-targeting Pack (Store)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> .NET 4.5.1 Redist<br /><br /> .NET 4.5.1 Redist Language Packs<br /><br /> .NET 4.5.1 SDK|  
|[ASP.NET Web Stack](https://support.microsoft.com/kb/2902020)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> Rozhraní ASP.NET Web API<br /><br /> Webové rozhraní API 2 technologie ASP.NET<br /><br /> ASP.NET Web Pages 2<br /><br /> ASP.NET – webové stránky 3|  
|[Entity Framework 6](https://support.microsoft.com/kb/2902020)|Entity Framework 6|  
|[Exchange 2013](https://support.microsoft.com/kb/2902020)|Webové služby Exchange|  
|[Microsoft OWIN](https://support.microsoft.com/kb/2902020)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](https://support.microsoft.com/kb/2902020)|Microsoft Web Developer Tools 2013|  
|Aktualizace těchto komponent se distribuují prostřednictvím rozšíření NuGet a jejich životní cyklus se neřídí standardními zásadami společnosti Microsoft.  Další informace najdete tady: [http://docs.nuget.org/](https://docs.microsoft.com/nuget/).|Obslužná rutina JSON Web Token pro Microsoft .NET Framework 4,5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](https://support.microsoft.com/kb/2902020)|ODataLib|  
|[Office 2013](https://support.microsoft.com/lifecycle/search/?p1=16674)|Open XML SDK|  
|[Zásady služeb Online Services](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy)|Microsoft Ads SDK|  
|[SharePoint 2013](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|SharePoint Client Component<br /><br /> SharePoint Foundation 2013<br /><br /> Windows Identity Foundation Extensions|  
|[Silverlight 5](https://support.microsoft.com/lifecycle/search/?p1=16278)<br /><br /> <br />> Viz také: [http://support.microsoft.com/gp/lifean45](https://support.microsoft.com/gp/lifean45)|Silverlight 5 Runtime<br /><br /> Silverlight 5 SDK|  
|[SQL Server 2008 R2](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|SQL System CLR Types (SQL Server 2008 R2)|  
|[SQL Server 2012](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL Command Line Utilities<br /><br /> Služba jazyka SQL – IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2012 SP1<br /><br /> SQL System CLR Types (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> SQL Command Line Utilities<br /><br /> Služba jazyka SQL – IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> SQL Native Client (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> SQL System CLR Types (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact edice 4,0](https://support.microsoft.com/lifecycle/search/?p1=16106)|SQL Server Compact Edition 4.0|  
|[Služby WCF RIA v 1.0 SP2](https://support.microsoft.com/kb/2902020)|WCF RIA Services v1.0 SP2|  
|[Windows Server 2008](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Windows Web Services (WWS) for Windows Server 2008|  
|[Windows 7](https://support.microsoft.com/lifecycle/search/?c2=14019)|Windows 7 SDK|  
|[Windows 8](https://support.microsoft.com/lifecycle/search/?c2=16796)|Windows 8 SDK|  
|[Windows 8.1](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Windows 8.1 SDK<br /><br /> knihovna Windows pro jazyk JavaScript (WinJS)|  
|[Microsoft Azure](https://support.microsoft.com/help/18486/lifecycle-faq-azure)<br /><br /> <br />> Viz také: [zásady online životního cyklu](https://support.microsoft.com/hub/4095338/microsoft-lifecycle-policy) .|Sada SDK Microsoft Azure Mobile Services<br /><br /> Nástroje Microsoft Azure Mobile Services|
