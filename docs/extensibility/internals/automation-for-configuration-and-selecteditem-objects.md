---
title: Automatizace pro objekty Configuration a SelectedItem | Microsoft Docs
description: Naučte se automatizovat procesy sestavení a vybrané položky sady Visual Studio pomocí objektů Configuration a SelectedItem v tématu interoperabilita prostředí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4a1316115ca3ebbd0f78249d1a73310fc06de688
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906077"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatizace pro objekty Configuration a SelectedItem

Procesy sestavení a vybrané položky můžete automatizovat v aplikaci Visual Studio.

## <a name="automation-for-builds"></a>Automatizace pro buildy

Sestavení nebo konfigurace má model automatizace, který je k dispozici při implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Další informace najdete v tématu [Principy konfigurací sestavení](../../ide/understanding-build-configurations.md).

Pokud vytvoříte VSPackage a chcete ovládat možnosti konfigurace, je nutné použít model automatizace.

## <a name="automation-for-selecteditem"></a>Automatizace pro SelectedItem

Není nutné zadávat implementaci `SelectedItem` objektu, protože aplikace Visual Studio obsahuje standardní implementaci. Pokud ale dáváte přednost, můžete `SelectedItem` objekt implementovat. Je nutné implementovat objekt, který obsahuje `SelectedItem` rozhraní a vrátit odpověď volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody s `VSITEMID` nastavením na [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Přispívání do modelu automatizace](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Vysvětlení konfigurací sestavení](../../ide/understanding-build-configurations.md)
