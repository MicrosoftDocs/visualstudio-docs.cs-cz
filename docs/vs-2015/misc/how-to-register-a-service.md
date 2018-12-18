---
title: 'Postupy: registrace služby | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: a1f8026a648b2a0809af17664d4399f815c329be
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206255"
---
# <a name="how-to-register-a-service"></a>Postupy: registrace služby
Rozhraní spravovaného balíčku (MPF) poskytuje atributy pro řízení registrace spravovaných služeb. Nástroj RegPkg používá tyto atributy pro registraci služby s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Příklad  
 Kód, který je z [VSSDK ukázky](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Registruje službu SMyGlobalService s [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Další informace o <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> a <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, naleznete v tématu [registrace a zrušení registrace rozšíření VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Pokud chcete zaregistrovat službu, která nahrazuje jinou se stejným názvem, použijte <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> místo <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Robustní programování  
 Aby bylo snazší znovu zkompilovat poskytovatele služeb beze změny klienta služby nebo naopak, můžete definovat službu a jeho rozhraní v samostatném sestavení modulu. Následující kód je ze souboru IMyGlobalService.cs v ukázce Reference.Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Je nutná k získání rozhraní z nespravovaného kódu.  
  
> [!NOTE]
>  I když můžete použít stejný typ nebo identifikátor GUID pro služby a rozhraní, doporučujeme oddělit dva, protože služba může vystavit různá rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Registrace balíčků VSPackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Základy služeb](../extensibility/internals/service-essentials.md)