---
title: Distribuce aplikací izolovaného prostředí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204667"
---
# <a name="distributing-isolated-shell-applications"></a>Distribuce aplikací izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby bylo možné vytvořit aplikaci izolovaného prostředí, je nutné nainstalovat sadu Visual Studio a sadu Visual Studio SDK. Chcete-li distribuovat aplikaci do počítačů jiných uživatelů nebo zákazníků, je nutné pro izolované prostředí zahrnout speciální Distribuovatelný balíček.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Předpoklady pro distribuci aplikací izolovaného prostředí  
  
|Název|Popis|  
|----------|-----------------|  
|Visual Studio SDK|Sada SDK, kterou potřebujete pro vývoj a testování rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Můžete také použít sadu SDK k vytvoření vlastní instance izolovaného prostředí sady Visual Studio.<br /><br /> Sada Visual Studio je předpokladem pro sadu SDK.|  
|Redistribuovatelná prostředí pro distribuci Microsoft Visual Studio|Distribuovatelný balíček, který zahrnete do instalačního programu při vytváření prostředí nástrojů v izolovaném prostředí sady Visual Studio. Distribuovatelný balíček izolovaného prostředí zahrnuje .NET Framework 4,5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Vytvoření instalačního programu pro aplikaci  
 Je nutné vytvořit speciální instalační program pro integrovanou nebo izolovanou aplikaci prostředí. Další informace najdete v tématu [instalace aplikace izolovaného prostředí](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Umožnění aktualizací vaší aplikace  
 Instalační program musí umožňovat, aby se vaše aplikace aktualizovala buď prostřednictvím aktualizací společnosti Microsoft, nebo podle aktualizací vaší společnosti. Další informace o aktualizacích najdete v tématu [pokyny k obsluze pro aplikace izolovaného prostředí](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
