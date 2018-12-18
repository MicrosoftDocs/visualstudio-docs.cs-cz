---
title: Experimentální instanci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b529ba3a0ea8b38a27d06e03ce15106cbd7512a5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787988"
---
# <a name="the-experimental-instance"></a>Experimentální instance
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K ochraně vašeho vývojového prostředí sady Visual Studio z neověřeného aplikací, které mohou změnit, VSSDK místo experimentální, který vám pomůže experimentovat. Při vývoji nových aplikací pomocí sady Visual Studio jako obvykle, ale spouštíte je pomocí tento experimentální instanci.  
  
 Každá aplikace, která obsahuje balíček VSIX spustí experimentální instanci sady Visual Studio v režimu ladění.  
  
 Pokud chcete spustit experimentální instanci sady Visual Studio mimo konkrétní řešení, spusťte následující příkaz v příkazovém okně:  
  
 "*\<Cestu instalace sady visual studio >* \Common7\IDE\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  Experimentální instanci jsou zapsána do registru pod `<version number>Exp` a `<version number>Exp_Config` uzly. Je třeba oblasti experimentální registru Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` a `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Doporučujeme při vývoji se spustit rozšíření v experimentální instanci aplikace. Při nasazení rozšíření, poběží v instanci vývoje. Další informace o registraci aplikace najdete v tématu [registrace rozšíření VSPackages](../extensibility/internals/registering-vspackages.md).

