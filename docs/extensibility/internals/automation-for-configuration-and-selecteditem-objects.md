---
title: Automatizace pro konfigurace a objekty SelectedItem | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709975"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatizace pro objekty Konfigurace a SelectedItem

Můžete automatizovat sestavení a vybrané položky procesy v sadě Visual Studio.

## <a name="automation-for-builds"></a>Automatizace pro sestavení

Sestavení nebo konfigurace má model automatizace, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>který je k dispozici při implementaci . Další informace naleznete v [tématu Understand build configurations](../../ide/understanding-build-configurations.md).

Pokud vytvoříte VSPackage a chcete řídit možnosti konfigurace, musíte použít model automatizace.

## <a name="automation-for-selecteditem"></a>Automatizace pro selecteditem

Není třeba poskytnout implementaci pro `SelectedItem` objekt, protože Visual Studio obsahuje standardní implementaci. Však můžete implementovat `SelectedItem` objekt, pokud dáváte přednost. Je nutné implementovat objekt, který obsahuje `SelectedItem` rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> vrátit `VSITEMID` odpověď na volání metody s nastavenou na [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Přispějte k modelu automatizace](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Vysvětlení konfigurací sestavení](../../ide/understanding-build-configurations.md)
