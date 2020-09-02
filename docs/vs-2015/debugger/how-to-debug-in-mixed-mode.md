---
title: 'Postupy: ladění ve smíšeném režimu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5e2dd4ea0000eefdbd9f74c8fa97c4c63e06fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681133"
---
# <a name="how-to-debug-in-mixed-mode"></a>Postupy: Ladění ve smíšeném režimu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Následující postupy popisují, jak ladit spravovaný i nativní kód, označovaný také jako ladění v kombinovaném režimu. Existují dva scénáře k tomu, v závislosti na tom, zda je knihovna DLL nebo aplikace napsána v nativním kódu:  
  
- Volající aplikace, která volá vaši knihovnu DLL, je zapsána v nativním kódu. V tomto případě je vaše knihovna DLL spravovaná a pro ladění obou musí být povolen jak spravovaný, tak nativní ladicí program. Můžete to vrátit v dialogovém okně ** \<Project> stránky vlastností** . Postup závisí na tom, zda jste spustili ladění z projektu knihovny DLL nebo projektu volání aplikace.  
  
- Volající aplikace, která volá vaši knihovnu DLL, je zapsána ve spravovaném kódu a vaše knihovna DLL je napsána v nativním kódu.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Povolení ladění ve smíšeném režimu  
  
1. V **Průzkumník řešení**vyberte projekt.  
  
2. V nabídce **zobrazení** klikněte na položku **stránky vlastností**.  
  
3. V dialogovém okně ** \<Project> stránky vlastností** rozbalte uzel **Vlastnosti konfigurace** a poté vyberte možnost **ladění**.  
  
4. Nastavte **Typ ladicího programu** na **Mixed** nebo **auto**.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Ladění z projektu knihovny DLL](../debugger/how-to-debug-from-a-dll-project.md)
