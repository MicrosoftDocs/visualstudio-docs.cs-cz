---
title: 'Postupy: automatické zvýšení verze publikování ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50faf70e8eda6ef7ab01201102540729497eb87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683926"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Postupy: Automatická inkrementace verze publikování ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při publikování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace Změna `Publish Version` vlastnosti způsobí, že se aplikace publikuje jako aktualizace. Ve výchozím nastavení Visual Studio automaticky zvyšuje `Revision` počet `Publish Version` pokaždé, když publikujete aplikaci.  
  
 Toto chování můžete zakázat na stránce **publikovat** v **Návrháři projektu**.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>Zakázání automatického zvýšení verze publikování  
  
1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. Klikněte na kartu **publikovat** .  
  
3. V části **publikovat verzi** zrušte zaškrtnutí políčka **automaticky zvyšovat revizi při každém vydání** .  
  
## <a name="see-also"></a>Viz také  
 [Postupy: nastavení verze publikování ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
