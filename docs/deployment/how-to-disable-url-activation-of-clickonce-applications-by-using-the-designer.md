---
title: 'Postupy: zákaz aktivace adresy URL aplikací ClickOnce pomocí návrháře | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97357dd92525be2d36b552c5f3df49080f46d29b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152031"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Postupy: zákaz aktivace adresy URL aplikací ClickOnce pomocí návrháře
Obvykle [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace se automaticky spustí ihned po jeho instalaci z webového serveru. Z bezpečnostních důvodů se můžete rozhodnout pro toto chování zakázat a že se uživatelé můžou spouštět aplikace z **Start** nabídky místo. Následující postup popisuje, jak zákaz aktivace adresy URL.  
  
 Tento postup lze použít pouze pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nainstalované v počítači uživatele z webového serveru. Nelze použít pro online jen pro aplikace, které lze spustit pouze pomocí jejich adresy URL. Další informace o rozdílech mezi pouze v režimu online a nainstalovaných aplikací, najdete v části [Výběr strategie nasazení ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Tento postup používá [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Tuto úlohu lze provést také pomocí [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Další informace najdete v tématu [postupy: zakázání aktivace adresy URL z aplikací ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Chcete-li zákaz aktivace adresy URL pro vaši aplikaci  
  
1.  Klikněte pravým tlačítkem na název vašeho projektu v **Průzkumníka řešení**a klikněte na tlačítko **vlastnosti**.  
  
2.  Na **vlastnosti** stránky, klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **možnosti**.  
  
4.  Klikněte na tlačítko **manifesty**.  
  
5.  Zaškrtněte políčko s popiskem **blokovat aplikaci při aktivaci prostřednictvím adresy URL**.  
  
6.  Při nasazování aplikace.  
  
## <a name="see-also"></a>Viz také:  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)