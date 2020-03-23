---
title: Sada nástrojů, karta Součásti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5eb8c320a3190121d95395f7b359aa9ed978408
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597305"
---
# <a name="toolbox-components-tab"></a>Panel nástrojů, karta Komponenty

Zobrazí součásti, které můžete přidat do návrhářů jazyka Visual Basic a C# pro Windows Forms. Kromě součástí .NET, které jsou součástí sady Visual <xref:System.Messaging.MessageQueue> Studio, jako jsou součásti a, <xref:System.Diagnostics.EventLog> můžete na tuto kartu přidat vlastní součásti nebo součásti jiných výrobců.

Chcete-li tuto kartu zobrazit, otevřete návrháře formulářů systému Windows. Vyberte **Zobrazit** > **panel nástrojů**. V **panelu nástrojů**vyberte kartu **Komponenty.**

## <a name="components"></a>Komponenty

**BackgroundWorker**

Vytvoří <xref:System.ComponentModel.BackgroundWorker> instanci komponenty, která může spustit operaci v samostatném vyhrazeném vlákně. Další informace naleznete v tématu [BackgroundWorker komponenty](/dotnet/framework/winforms/controls/backgroundworker-component).

**Directoryentry**

Vytvoří <xref:System.DirectoryServices.DirectoryEntry> instanci komponenty, která zapouzdřuje uzel nebo objekt v hierarchii služby Active Directory a lze ji použít k interakci s poskytovateli služeb Active Directory.

**DirectorySearcher**

Vytvoří <xref:System.DirectoryServices.DirectorySearcher> instanci komponenty, kterou můžete použít k provádění dotazů proti službě Active Directory.

**ErrorProvider**

Vytvoří <xref:System.Windows.Forms.ErrorProvider> instanci komponenty, která koncovému uživateli ukazuje, že ovládací prvek ve formuláři má přidruženou chybu. Další informace naleznete v tématu [ErrorProvider component](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**Eventlog**

Vytvoří <xref:System.Diagnostics.EventLog> instanci komponenty, kterou můžete použít k interakci se systémovými protokoly a protokoly vlastních událostí, včetně zápisu událostí do protokolu a čtení dat protokolu.

**Filesystemwatcher**

Vytvoří <xref:System.IO.FileSystemWatcher> instanci komponenty, kterou můžete použít ke sledování změn v libovolném adresáři nebo souboru, ke kterému máte přístup.

**Helpprovider**

Vytvoří <xref:System.Windows.Forms.HelpProvider> instanci komponenty, která poskytuje automaticky otevíraná data nebo online nápovědu pro ovládací prvky. Další informace naleznete v tématu [HelpProvider component](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**Imagelist**

Vytvoří <xref:System.Windows.Forms.ImageList> instanci komponenty, která <xref:System.Drawing.Image> poskytuje metody pro správu kolekce objektů. Další informace naleznete v [tématu ImageList komponenty](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**Messagequeue**

Vytvoří <xref:System.Messaging.MessageQueue> instanci komponenty, kterou můžete použít k interakci s frontami zpráv, včetně čtení zpráv a zápisu zpráv do front, zpracování transakcí a provádění úloh správy fronty.

**Performancecounter**

Vytvoří <xref:System.Diagnostics.PerformanceCounter> instanci komponenty, kterou můžete použít k interakci s čítači výkonu systému Windows, včetně vytváření nových kategorií a instancí, čtení hodnot z čítačů a provádění výpočtů dat čítačů.

**Proces**

Vytvoří <xref:System.Diagnostics.Process> instanci komponenty, kterou můžete použít k zastavení, spuštění a manipulaci s daty přidruženými k procesům v systému.

**Serialport**

Vytvoří <xref:System.IO.Ports.SerialPort> instanci komponenty, která poskytuje synchronní a událostmi řízené vstupně-videa, přístup ke stavům pin a break a přístup k vlastnostem sériového ovladače.

**Servicecontroller**

Vytvoří <xref:System.ServiceProcess.ServiceController> instanci komponenty, kterou můžete použít k manipulaci s existujícími službami, včetně spouštění a zastavování služeb a odesílání příkazů.

**Časovač**

Vytvoří <xref:System.Windows.Forms.Timer> instanci komponenty, kterou můžete použít k přidání funkcí založených na čase do aplikací systému Windows. Další informace naleznete v tématu [Timer component](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> K dispozici je také <xref:System.Timers.Timer> systém založený, který můžete <xref:System.Timers.Timer> přidat do **panelu nástrojů** To <xref:System.Windows.Forms.Timer> je optimalizováno pro serverové aplikace a Windows Forms je nejvhodnější pro použití ve windows forms.

## <a name="see-also"></a>Viz také

- [Ovládací prvky pro použití ve Formulářích Systému Windows](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Zvolte položky panelu nástrojů, součásti WPF](choose-toolbox-items-wpf-components.md)
- [Sada nástrojů](../../ide/reference/toolbox.md)
