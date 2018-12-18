---
title: Protokolování události u řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 267d3e06e9f0d4733a7985f65aa81f368c3f5413
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925109"
---
# <a name="event-logging-for-office-solutions"></a>Protokolování události u řešení pro systém Office
  Můžete v prohlížeči událostí ve Windows najdete v článku zprávy o výjimkách, které jsou zachyceny [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] při instalaci nebo odinstalaci řešení Office. Tyto zprávy z protokolování událostí můžete použít k vyřešení instalace a problémů s nasazením.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="read-the-event-log"></a>Přečíst protokol událostí  
 Otevřít **Prohlížeč událostí** a filtrování pro události, které chcete zobrazit.  
  
### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Přečíst protokol událostí systému Windows Server 2003 a Windows XP  
  
1.  V Ovládacích panelech otevřete **nástroje pro správu**.  
  
2.  Spustit **Prohlížeč událostí**.  
  
3.  Vyberte v seznamu protokolů událostí **aplikace**.  
  
4.  Na **zobrazení** nabídky, klikněte na tlačítko **filtr**.  
  
5.  V **zdroj události** seznamu vyberte **VSTO 4.0**.  
  
6.  Pro instalaci události v **ID události** zadejte **4096**.  
  
7.  Klikněte na tlačítko **OK** zobrazíte filtrované zobrazení.  
  
### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Přečíst protokol událostí ve Windows 7, Windows Vista a Windows Server 2008  
  
1. V Ovládacích panelech otevřete **nástroje pro správu**.  
  
2. Spustit **Prohlížeč událostí**.  
  
3. Rozbalte **protokoly Windows**.  
  
4. Vyberte v seznamu protokolů událostí **aplikace**.  
  
5. Na **akce** nabídky, klikněte na tlačítko **filtrovat aktuální protokol**.  
  
6. V **zdroj události** seznamu vyberte **VSTO 4.0**.  
  
7. Pro instalaci události v **ID události** zadejte **4096**.  
  
8. Klikněte na tlačítko **OK** zobrazíte filtrované zobrazení.  
  
   V prohlížeči událostí obsahuje tyto informace:  
  
- Umístění manifestu nasazení pro řešení.  
  
- Zpráva, která popisuje příčinu chyby nebo výjimky.  
  
  Tyto zprávy o výjimkách, můžete zjistit, proč pro problém s instalací, například na nedůvěryhodný certifikát, umístění služby nedůvěryhodné dokumentu nebo manifest nasazení je neplatná.  
  
  Po odinstalaci je řešení pro Office, zůstanou zprávy o výjimce v protokolu událostí.  
  
  Zobrazit nebo protokolování výjimek zpráv při spuštění řešení pro Office naleznete v tématu [projekty Office ladění](../vsto/debugging-office-projects.md) a [projekty Office ladění](../vsto/debugging-office-projects.md).  
  
### <a name="localization"></a>Lokalizace  
 Visual Studio Tools for Office runtime language Určuje jazyk zpráva o výjimce. Například pokud má počítač koncového uživatele japonská jazyková sada nainstalovaná, zpráva výjimky je zapsané do protokolu událostí v japonštině.  
  
## <a name="disable-the-event-logger"></a>Zakázat protokolování událostí  
 Ve výchozím nastavení je protokolování událostí při instalaci nebo odinstalaci řešení pro systém Office povolené. Protokolování událostí můžete zakázat nastavením proměnné prostředí VSTO_EVENTLOGDISABLED "1" (jeden).  
  
### <a name="to-disable-the-event-log"></a>Chcete-li zakázat protokol událostí  
  
1.  V Ovládacích panelech otevřete **systému**.  
  
2.  Na **Upřesnit** klikněte na tlačítko **proměnné prostředí**.  
  
3.  V **systémové proměnné** podokně klikněte na tlačítko **nový**.  
  
4.  V **nová systémová proměnná** dialogovém okně **VSTO_EVENTLOGDISABLED** v **název proměnné** pole.  
  
5.  V **hodnotu proměnné** zadejte **1**.  
  
6.  Klikněte na tlačítko **OK**.  
  
## <a name="see-also"></a>Viz také:  
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Řešení potíží s nasazením řešení pro systém Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  