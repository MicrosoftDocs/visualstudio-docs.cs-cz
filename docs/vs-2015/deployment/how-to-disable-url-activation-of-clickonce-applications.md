---
title: 'Postupy: zákaz aktivace adresy URL aplikací ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75a98706858323693ec01ec3c3420a6d2d25ffef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697216"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Postupy: Zákaz aktivace adresy URL aplikací ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obvykle se [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace automaticky spustí hned po instalaci z webového serveru. Z bezpečnostních důvodů se můžete rozhodnout toto chování zakázat a uživatelům sdělit, aby aplikaci spustili z nabídky **Start** . Následující postup popisuje, jak zakázat aktivaci adresy URL.  
  
 Tato technika se dá použít jenom pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace nainstalované v počítači uživatele z webového serveru. Nedá se použít jenom pro online aplikace, které se dají spustit jenom pomocí jejich adresy URL. Další informace o rozdílu mezi online a nainstalovanými aplikacemi najdete v tématu [volba strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Tato procedura používá [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] nástroj MageUI.exe. Další informace o tomto nástroji najdete v tématu [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Tento postup můžete provést také pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Zakázání aktivace adresy URL pro vaši aplikaci  
  
1. Otevřete manifest nasazení v MageUI.exe. Pokud jste ho ještě nevytvořili, postupujte podle kroků v [návodu: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2. Vyberte kartu **Možnosti nasazení** .  
  
3. Zrušte zaškrtnutí políčka **automaticky spouštět aplikaci po instalaci** .  
  
4. Uložte manifest a podepište ho.  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
