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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd9c6bf4d24a681c426a20f490dba2cc1d5080fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644597"
---
# <a name="toolbox-components-tab"></a>Panel nástrojů, karta součásti

Zobrazí komponenty, které můžete přidat do Visual Basic C# a návrháře pro model Windows Forms. Kromě součástí .NET, které jsou součástí sady Visual Studio, jako jsou například <xref:System.Messaging.MessageQueue> a <xref:System.Diagnostics.EventLog> komponenty, můžete na tuto kartu přidat vlastní součásti nebo komponenty třetích stran.

Chcete-li zobrazit tuto kartu, otevřete model Windows Forms Designer. Vyberte **zobrazení**  > **Sada nástrojů**. Na **panelu nástrojů**vyberte kartu **součásti** .

## <a name="components"></a>Komponenty

**BackgroundWorker**

Vytvoří instanci komponenty <xref:System.ComponentModel.BackgroundWorker>, která může spustit operaci na samostatném vyhrazeném vlákně. Další informace najdete v tématu [Komponenta BackgroundWorker](/dotnet/framework/winforms/controls/backgroundworker-component).

**Třída**

Vytvoří instanci <xref:System.DirectoryServices.DirectoryEntry> komponenty, která zapouzdřuje uzel nebo objekt v hierarchii služby Active Directory a dá se použít k interakci s poskytovateli služeb Active Directory.

**Rámci**

Vytvoří instanci komponenty <xref:System.DirectoryServices.DirectorySearcher>, kterou můžete použít k provádění dotazů na službu Active Directory.

**ErrorProvider**

Vytvoří instanci <xref:System.Windows.Forms.ErrorProvider> komponenty, která indikuje koncovému uživateli, že k ovládacímu prvku na formuláři je přidružená chyba. Další informace najdete v tématu [Komponenta ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Vytvoří instanci komponenty <xref:System.Diagnostics.EventLog>, kterou můžete použít k interakci se systémovými a vlastními protokoly událostí, včetně zápisu událostí do protokolu a čtení dat protokolu.

**FileSystemWatcher**

Vytvoří instanci komponenty <xref:System.IO.FileSystemWatcher>, kterou můžete použít k monitorování změn v jakémkoli adresáři nebo souboru, ke kterému máte přístup.

**HelpProvider –**

Vytvoří instanci <xref:System.Windows.Forms.HelpProvider> komponenty, která poskytuje místní nebo online nápovědu pro ovládací prvky. Další informace najdete v tématu [Komponenta HelpProvider –](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**Obrázků**

Vytvoří instanci <xref:System.Windows.Forms.ImageList> komponenty, která poskytuje metody pro správu kolekce objektů <xref:System.Drawing.Image>. Další informace najdete v tématu [Komponenta ImageList](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Vytvoří instanci <xref:System.Messaging.MessageQueue> komponenty, kterou můžete použít k interakci s frontami zpráv, včetně čtení zpráv z front a zápisů do front, zpracování transakcí a provádění úloh správy fronty.

**PerformanceCounter**

Vytvoří instanci <xref:System.Diagnostics.PerformanceCounter> komponenty, kterou můžete použít k interakci s čítači výkonu systému Windows, včetně vytváření nových kategorií a instancí, čtení hodnot z čítačů a provádění výpočtů s daty čítače.

**Přihlášení**

Vytvoří instanci <xref:System.Diagnostics.Process> komponenty, kterou můžete použít k zastavení, spuštění a manipulaci s daty přidruženými k procesům ve vašem systému.

**Portu SerialPort**

Vytvoří instanci <xref:System.IO.Ports.SerialPort> komponenty, která poskytuje synchronní a vstupně-výstupní operace řízené událostmi, přístup k stavům PIN a přerušení a přístup k vlastnostem sériového ovladače.

**ServiceController**

Vytvoří instanci <xref:System.ServiceProcess.ServiceController> komponenty, kterou můžete použít k manipulaci s existujícími službami, včetně spouštění a zastavování služeb a posílání příkazů do nich.

**Timer**

Vytvoří instanci <xref:System.Windows.Forms.Timer> komponenty, kterou můžete použít k přidání časových funkcí do aplikací určených pro systém Windows. Další informace najdete v tématu [Komponenta Timer](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> K dispozici je také systém <xref:System.Timers.Timer>, který lze přidat do **sady nástrojů** . Tato <xref:System.Timers.Timer> je optimalizována pro serverové aplikace a model Windows Forms <xref:System.Windows.Forms.Timer> je nejvhodnější pro použití na model Windows Forms.

## <a name="see-also"></a>Viz také:

- [Ovládací prvky pro použití na model Windows Forms](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Zvolit položky panelu nástrojů, komponenty WPF](choose-toolbox-items-wpf-components.md)
- [Panel nástrojů](../../ide/reference/toolbox.md)