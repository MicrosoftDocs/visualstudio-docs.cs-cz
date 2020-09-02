---
title: Protokolování událostí pro řešení pro systém Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 480a355ee2af321341c54b90edcc582d49102186
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62951931"
---
# <a name="event-logging-for-office-solutions"></a>Protokolování událostí pro řešení pro systém Office
  Prohlížeč událostí ve Windows můžete použít k zobrazení zpráv výjimek, které jsou zachyceny [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] při instalaci nebo odinstalaci řešení Office. Pomocí těchto zpráv z protokolovacího nástroje můžete vyřešit problémy s instalací a nasazením.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="read-the-event-log"></a>Přečtěte si protokol událostí.
 Otevřete **Prohlížeč událostí** a vyfiltrujte události, které chcete zobrazit.

### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Postup čtení protokolu událostí v systému Windows Server 2003 a Windows XP

1. V Ovládacích panelech otevřete **Nástroje pro správu**.

2. Spusťte **Prohlížeč událostí**.

3. V seznamu protokolů událostí vyberte **Application (aplikace**).

4. V nabídce **zobrazení** klikněte na možnost **Filtr**.

5. V seznamu **zdroj události** vyberte **VSTO 4,0**.

6. V případě událostí instalace zadejte do pole **ID události** **4096**.

7. Kliknutím na tlačítko **OK** zobrazíte filtrované zobrazení.

### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Postup čtení protokolu událostí v systému Windows 7, Windows Vista a Windows Server 2008

1. V Ovládacích panelech otevřete **Nástroje pro správu**.

2. Spusťte **Prohlížeč událostí**.

3. Rozbalte položku **protokoly systému Windows**.

4. V seznamu protokolů událostí vyberte **Application (aplikace**).

5. V nabídce **Akce** klikněte na možnost **Filtrovat aktuální protokol**.

6. V seznamu **zdroj události** vyberte **VSTO 4,0**.

7. V případě událostí instalace zadejte do pole **ID události** **4096**.

8. Kliknutím na tlačítko **OK** zobrazíte filtrované zobrazení.

   Prohlížeč událostí obsahuje následující informace:

- Umístění manifestu nasazení pro řešení.

- Zpráva, která popisuje příčinu chyby nebo výjimky.

  Tyto zprávy o výjimce vám mohou přispět k určení příčiny problému s instalací, jako je nedůvěryhodný certifikát, nedůvěryhodné umístění dokumentu nebo neplatný manifest nasazení.

  Po odinstalaci řešení pro systém Office zůstanou zprávy o výjimkách v protokolu událostí.

  Chcete-li zobrazit nebo zaznamenat zprávy o výjimce při spuštění řešení Office, přečtěte si téma [ladění projektů Office](../vsto/debugging-office-projects.md) a [ladění projektů Office](../vsto/debugging-office-projects.md).

### <a name="localization"></a>Lokalizace
 Jazyk zprávy o výjimce je určen jazykem Visual Studio Tools for Office runtime. Pokud má například počítač koncového uživatele nainstalované japonské jazykové sady, zpráva o výjimce se zapíše do protokolu událostí v japonštině.

## <a name="disable-the-event-logger"></a>Zakázání protokolovacího nástroje událostí
 Ve výchozím nastavení je protokolovací nástroj povolený při instalaci nebo odinstalaci řešení Office. Nástroj pro protokolování událostí můžete zakázat nastavením proměnné prostředí VSTO_EVENTLOGDISABLED na hodnotu 1 (jedna).

### <a name="to-disable-the-event-log"></a>Zakázání protokolu událostí

1. V Ovládacích panelech otevřete **systém**.

2. Na kartě **Upřesnit** klikněte na **proměnné prostředí**.

3. V podokně **systémové proměnné** klikněte na **Nový**.

4. V dialogovém okně **Nová systémová proměnná** zadejte do pole **název proměnné** **VSTO_EVENTLOGDISABLED** .

5. Do pole **Proměnná hodnota** zadejte **1**.

6. Klikněte na **OK**.

## <a name="see-also"></a>Viz také
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Řešení potíží s nasazením řešení pro systém Office](../vsto/troubleshooting-office-solution-deployment.md)
