---
title: Automatizace pro objekty Configuration a SelectedItem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157256"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatizace pro konfiguraci a objekty SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Procesy sestavení a vybrané položky můžete automatizovat v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>Automatizace pro buildy  
 Sestavení nebo konfigurace má model automatizace, který je k dispozici při implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Další informace najdete v tématu [Principy konfigurací sestavení](../../ide/understanding-build-configurations.md).  
  
 Pokud vytvoříte VSPackage a chcete ovládat možnosti konfigurace, je nutné použít model automatizace.  
  
## <a name="automation-for-selecteditem"></a>Automatizace pro SelectedItem  
 Není nutné zadávat implementaci `SelectedItem` objektu, protože aplikace Visual Studio obsahuje standardní implementaci. Pokud ale dáváte přednost, můžete `SelectedItem` objekt implementovat. Je nutné implementovat objekt, který obsahuje `SelectedItem` rozhraní a vrátit odpověď volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody s VSITEMID nastavenou na <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Přispívání do modelu automatizace](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Principy konfigurací sestavení](../../ide/understanding-build-configurations.md)
