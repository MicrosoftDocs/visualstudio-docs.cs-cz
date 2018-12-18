---
title: Distribuce aplikací izolovaného prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27228131c1e955a394e666ac05f0ddd68c879be0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758780"
---
# <a name="distributing-isolated-shell-applications"></a>Distribuce aplikací izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li vytvořit aplikací izolovaného prostředí musíte nainstalovat Visual Studio a Visual Studio SDK. K distribuci aplikace na počítače jiných uživatelů nebo zákazníků, musí obsahovat speciální distribuovatelných balíčků pro izolovaného prostředí.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Požadavky distribuce aplikací izolovaného prostředí  
  
|Název|Popis|  
|----------|-----------------|  
|Visual Studio SDK|Sady SDK potřebujete pro vývoj a testování rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Sady SDK můžete použít také k vytvoření vlastní instance sady Visual Studio izolované prostředí.<br /><br /> Visual Studio je předpokladem pro sadu SDK.|  
|Izolované prostředí distribuovatelné součásti Microsoft Visual Studio|Redistribuovatelný balíček při vytváření prostředí pro nástroje v sadě Visual Studio zahrnují ve vašem instalačním programu izolované prostředí. Distribuovatelný balíček rozhraní izolovaného prostředí zahrnuje rozhraní .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Vytváření instalačního programu pro aplikaci  
 Je nutné vytvořit zvláštní instalační program pro vaši aplikaci integrované nebo izolované prostředí. Další informace najdete v tématu [instalace izolované aplikační prostředí](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Povolení aktualizací do vaší aplikace  
 Instalační program musíte povolit možnost, že vaše aplikace bude aktualizován, aktualizace od Microsoftu nebo aktualizace vaší společnosti. Další informace o aktualizacích naleznete v tématu [pokyny údržbu aplikací izolovaného prostředí](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).

