---
title: 'Postupy: registrace služby | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: f41578f2522487f746a469933a2269a621390f3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64784858"
---
# <a name="how-to-register-a-service"></a>Postupy: registrace služby
Sada Managed Package Framework (MPF) poskytuje atributy pro kontrolu registrace spravovaných služeb. Nástroj RegPkg používá tyto atributy k registraci služby v nástroji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="example"></a>Příklad  
 Kód, který následuje, pochází z [VSSDK Samples](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>Registruje službu SMyGlobalService s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Další informace o <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> a <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> najdete v tématu [registrace a zrušení registrace VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Chcete-li zaregistrovat službu, která nahrazuje jinou službu se stejným názvem, použijte <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> místo <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> .  
  
## <a name="robust-programming"></a>Robustní programování  
 Aby bylo snazší znovu kompilovat poskytovatele služby beze změny klienta služby nebo naopak, můžete definovat službu a její rozhraní v samostatném modulu sestavení. Následující kód je ze souboru IMyGlobalService.cs v ukázce reference. Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>Je vyžadován k získání rozhraní z nespravovaného kódu.  
  
> [!NOTE]
> I když můžete použít stejný typ nebo identifikátor GUID jak pro službu, tak pro rozhraní, doporučujeme, abyste tyto dvě oddělení odlišili, protože služba může vystavovat různá rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Registrace VSPackage](../extensibility/internals/registering-vspackages.md)   
 [Základy služeb](../extensibility/internals/service-essentials.md)