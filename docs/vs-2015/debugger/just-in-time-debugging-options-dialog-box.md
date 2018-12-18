---
title: Just-In-Time, ladění, dialogové okno Možnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06fdd9d12003053ea6d992aa1d7d0fe9ed7144d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788131"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Za běhu, ladění, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pro přístup **Just-In-Time** stránky, přejděte na **nástroje** nabídky a klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **ladění** uzel a vyberte možnost **Just-In-Time**. Tato stránka umožňuje povolit Just-In-Time ladění pro spravovaný kód, nativního kódu a skriptů. Další informace najdete v tématu [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Můžete povolit Just-In-Time ladění pro tyto typy programu:  
  
- Spravované  
  
- Nativní  
  
- skript  
  
  Ladění Just-In-Time je postup pro ladění programu, který je spuštěn mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Můžete spustit aplikaci vytvořen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prostředí. Pokud jste povolili Just-in-time ladění, chyby se zobrazí dialogové okno s dotazem, zda chcete ladit.  
  
## <a name="associated-warnings"></a>Související upozornění  
 Při návštěvě této stránky **možnosti** dialogové okno, může se zobrazit zpráva s upozorněním takto:  
  
 **Jiný ladicí program se registroval jako Just-In-Time debugger. Pokud chcete opravit, povolte Just-In-Time ladění nebo spuštěním opravy sady Visual Studio.**  
  
 Tato zpráva se zobrazí, pokud máte jiný ladicí program, případně starší verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ladicího programu, nastavit jako Just-In-Time debugger.  
  
 Další zprávu, zobrazí se pravděpodobně vypadá takto:  
  
 **Just-In-Time ladění registrace byly zjištěny chyby. Pokud chcete opravit, povolte Just-In-Time ladění nebo spuštěním opravy sady Visual Studio.**  
  
 Pokud se zobrazí některá z těchto upozornění Just-In-Time ladění pomocí [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] vyžaduje oprávnění správce, dokud nebude tento problém opravili. Pokud se pokusíte povolit pouze – jako bez oprávnění správce za těchto podmínek, zobrazí se následující chybová zpráva:  
  
 **Přístup byl odepřen. Nemáte povolení Just-In-Time správce ladění nebo opravte instalaci sady Visual Studio.**  
  
## <a name="see-also"></a>Viz také  
 [Ladění, dialogové okno Možnosti](../debugger/debugging-options-dialog-box.md)   
 [Postupy: Určení nastavení ladicího programu](../debugger/how-to-specify-debugger-settings.md)



