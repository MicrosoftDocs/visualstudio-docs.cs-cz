---
title: Předpoklady pro vzdálené ladění webových aplikací | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8cbf0ae920be00980d270aae16d5e7d1f7a5313
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574631"
---
# <a name="prerequisites-for-remote-debugging-web-applications"></a>Předpoklady pro vzdálené ladění webových aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí ladicího programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] můžete webovou aplikaci transparentně ladit na místním počítači nebo na vzdáleném serveru. To znamená, že ladicí program funguje stejným způsobem a umožňuje používat stejné funkce na každém počítači. Aby vzdálené ladění fungovalo správně, existují ale nějaké požadavky.  
  
- na serveru, který chcete ladit, musí být nainstalované komponenty vzdáleného ladění [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Další informace najdete v tématu [Nastavení vzdáleného ladění](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
- Ve výchozím nastavení se pracovní proces [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] spouští jako proces uživatele ASPNET. V důsledku toho musíte mít v počítači, na kterém [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] spouští k ladění, oprávnění správce. Název pracovního procesu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] se liší podle scénáře ladění a verze služby IIS. Další informace najdete v tématu [Postupy: hledání názvu procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Viz také  
 [Ladění aplikací ASP.NET a AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)    
 [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md)
