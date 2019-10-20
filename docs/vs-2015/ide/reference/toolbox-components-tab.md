---
title: Sada nástrojů, karta součásti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce18767d95b3ac539737d78acbd2259dcda0a036
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661571"
---
# <a name="toolbox-components-tab"></a>Sada nástrojů, karta Součásti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zobrazí komponenty, které lze přidat do [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] a [!INCLUDE[csprcs](../../includes/csprcs-md.md)] návrháři. Kromě součástí [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], které jsou součástí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], jako jsou <xref:System.Messaging.MessageQueue> a <xref:System.Diagnostics.EventLog>, můžete na tuto kartu přidat vlastní nebo jiné komponenty třetích stran. Další informace naleznete v tématu [How to: manipulace s kartami nástrojů](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Chcete-li zobrazit tuto kartu, v nabídce **zobrazení** vyberte položku **Sada nástrojů**. V sadě **nástrojů**vyberte kartu **součásti** .

 **BackgroundWorker** Vytvoří instanci komponenty `System.ComponentModel.BackgroundWorker`, která může spustit operaci na samostatném vyhrazeném vlákně.

 Třída **DirectoryEntry** Vytvoří instanci <xref:System.DirectoryServices.DirectoryEntry> komponenty, která zapouzdřuje uzel nebo objekt v hierarchii služby Active Directory a dá se použít k interakci s poskytovateli služeb Active Directory.

 **Rámci** Vytvoří instanci komponenty <xref:System.DirectoryServices.DirectorySearcher>, kterou můžete použít k provádění dotazů na službu Active Directory.

 **ErrorProvider** Vytvoří instanci `System.Windows.Forms.ErrorProvider` komponenty, která indikuje koncovému uživateli, že k ovládacímu prvku na formuláři je přidružená chyba.

 Protokol **událostí** Vytvoří instanci komponenty <xref:System.Diagnostics.EventLog>, kterou můžete použít k interakci se systémovými a vlastními protokoly událostí, včetně zápisu událostí do protokolu a čtení dat protokolu. Další informace najdete v tématu [Úvod do komponenty EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Vytvoří instanci komponenty <xref:System.IO.FileSystemWatcher>, kterou můžete použít k monitorování změn v jakémkoli adresáři nebo souboru, ke kterému máte přístup. Další informace naleznete v tématu [How to: Configure a instance Component Instances FileSystemWatcher](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider –** Vytvoří instanci `System.Windows.Forms.HelpProvider` komponenty, která poskytuje místní nebo online nápovědu pro ovládací prvky.

 Seznam **ImageList** Vytvoří instanci `System.Windows.Forms.ImageList` komponenty, která poskytuje metody pro správu kolekce objektů `System.Drawing.Image`.

 **MessageQueue** Vytvoří instanci <xref:System.Messaging.MessageQueue> komponenty, kterou můžete použít k interakci s frontami zpráv, včetně čtení zpráv z front a zápisů do front, zpracování transakcí a provádění úloh správy fronty. Další informace najdete v tématu [použití součástí zasílání zpráv](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **PerformanceCounter** Vytvoří instanci <xref:System.Diagnostics.PerformanceCounter> komponenty, kterou můžete použít k interakci s čítači výkonu systému Windows, včetně vytváření nových kategorií a instancí, čtení hodnot z čítačů a provádění výpočtů s daty čítače. Další informace najdete v tématu [monitorování mezních hodnot výkonu](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Zpracování** Vytvoří instanci <xref:System.Diagnostics.Process> komponenty, kterou můžete použít k zastavení, spuštění a manipulaci s daty přidruženými k procesům ve vašem systému. Další informace najdete v tématu [monitorování a správa procesů systému Windows](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **Portu SerialPort** Vytvoří instanci `System.IO.Ports.SerialPort` komponenty, která poskytuje synchronní a vstupně-výstupní operace řízené událostmi, přístup k stavům PIN a přerušení a přístup k vlastnostem sériového ovladače.

 **ServiceController** Vytvoří instanci <xref:System.ServiceProcess.ServiceController> komponenty, kterou můžete použít k manipulaci s existujícími službami, včetně spouštění a zastavování služeb a posílání příkazů do nich. Další informace najdete v tématu [monitorování služeb systému Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Časovač** Vytvoří instanci <xref:System.Windows.Forms.Timer> komponenty, kterou můžete použít k přidání časových funkcí do aplikací určených pro systém Windows. Další informace najdete v tématu [Komponenta Timer](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> K dispozici je také systém <xref:System.Timers.Timer>, který lze přidat do **sady nástrojů** . Tato <xref:System.Timers.Timer> je optimalizována pro serverové aplikace a model Windows Forms <xref:System.Windows.Forms.Timer> je nejvhodnější pro použití na model Windows Forms.

## <a name="see-also"></a>Viz také
 [Programování pomocí](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [nástrojů](../../ide/reference/toolbox.md) průvodce [programováním](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) pro součásti komponent [dialogové okno zvolit položky panelu nástrojů (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
