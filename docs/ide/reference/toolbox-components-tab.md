---
title: Sada nástrojů, karta Součásti
description: Přečtěte si informace o komponentách, které najdete na kartě komponenty v okně panelu nástrojů.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 40ba84712a343a071d6213dc9cd985727fc20ebf
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560938"
---
# <a name="toolbox-components-tab"></a>Panel nástrojů, karta součásti

Zobrazí komponenty, které lze přidat do Visual Basic a návrháře jazyka C# pro model Windows Forms. Kromě součástí .NET, které jsou součástí sady Visual Studio, jako jsou například <xref:System.Messaging.MessageQueue> <xref:System.Diagnostics.EventLog> komponenty a, můžete na tuto kartu přidat vlastní součásti nebo komponenty třetích stran.

Chcete-li zobrazit tuto kartu, otevřete model Windows Forms Designer. Vyberte **zobrazení**  >  **sady nástrojů**. Na **panelu nástrojů** vyberte kartu **součásti** .

## <a name="components"></a>Komponenty

**BackgroundWorker**

Vytvoří <xref:System.ComponentModel.BackgroundWorker> instanci komponenty, která může spustit operaci na samostatném vyhrazeném vlákně. Další informace najdete v tématu [Komponenta BackgroundWorker](/dotnet/framework/winforms/controls/backgroundworker-component).

**Třída**

Vytvoří <xref:System.DirectoryServices.DirectoryEntry> instanci komponenty, která zapouzdřuje uzel nebo objekt v hierarchii služby Active Directory a dá se použít k interakci s poskytovateli služeb Active Directory.

**Rámci**

Vytvoří <xref:System.DirectoryServices.DirectorySearcher> instanci komponenty, kterou můžete použít k provádění dotazů na službu Active Directory.

**ErrorProvider**

Vytvoří <xref:System.Windows.Forms.ErrorProvider> instanci komponenty, která indikuje koncovému uživateli, že k ovládacímu prvku na formuláři je přidružena chyba. Další informace najdete v tématu [Komponenta ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Vytvoří <xref:System.Diagnostics.EventLog> instanci komponenty, kterou můžete použít k interakci se systémovými a vlastními protokoly událostí, včetně zápisu událostí do protokolu a čtení dat protokolu.

**FileSystemWatcher**

Vytvoří <xref:System.IO.FileSystemWatcher> instanci komponenty, kterou můžete použít k monitorování změn v jakémkoli adresáři nebo souboru, ke kterému máte přístup.

**HelpProvider –**

Vytvoří <xref:System.Windows.Forms.HelpProvider> instanci komponenty, která poskytuje místní nebo online nápovědu pro ovládací prvky. Další informace najdete v tématu [Komponenta HelpProvider –](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**Obrázků**

Vytvoří <xref:System.Windows.Forms.ImageList> instanci komponenty, která poskytuje metody pro správu kolekce <xref:System.Drawing.Image> objektů. Další informace najdete v tématu [Komponenta ImageList](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Vytvoří <xref:System.Messaging.MessageQueue> instanci komponenty, kterou můžete použít k interakci s frontami zpráv, včetně čtení zpráv a zápisů do front, zpracování transakcí a provádění úloh správy fronty.

**PerformanceCounter**

Vytvoří <xref:System.Diagnostics.PerformanceCounter> instanci komponenty, kterou můžete použít k interakci s čítači výkonu systému Windows, včetně vytváření nových kategorií a instancí, čtení hodnot z čítačů a provádění výpočtů s daty čítače.

**Proces**

Vytvoří <xref:System.Diagnostics.Process> instanci komponenty, kterou můžete použít k zastavení, spuštění a manipulaci s daty přidruženými k procesům ve vašem systému.

**Portu SerialPort**

Vytvoří <xref:System.IO.Ports.SerialPort> instanci komponenty, která poskytuje synchronní a vstupně-výstupní operace řízené událostmi, přístup k stavům PIN a přerušení a přístup k vlastnostem sériového ovladače.

**ServiceController**

Vytvoří <xref:System.ServiceProcess.ServiceController> instanci komponenty, kterou můžete použít k manipulaci s existujícími službami, včetně spouštění a zastavování služeb a posílání příkazů do nich.

**Časovač**

Vytvoří <xref:System.Windows.Forms.Timer> instanci komponenty, kterou můžete použít k přidání časových funkcí do aplikací založených na systému Windows. Další informace najdete v tématu [Komponenta Timer](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> K dispozici je také systém založený <xref:System.Timers.Timer> na systému, který lze přidat do **sady nástrojů** <xref:System.Timers.Timer> , což je optimalizováno pro serverové aplikace a model Windows Forms <xref:System.Windows.Forms.Timer> je nejvhodnější pro použití v model Windows Forms.

## <a name="see-also"></a>Viz také:

- [Ovládací prvky pro použití na model Windows Forms](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Výběr položek sady nástrojů, součásti WPF](choose-toolbox-items-wpf-components.md)
- [Sada nástrojů](../../ide/reference/toolbox.md)
