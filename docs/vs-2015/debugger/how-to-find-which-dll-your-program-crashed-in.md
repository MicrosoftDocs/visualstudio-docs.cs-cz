---
title: 'Postupy: hledání knihovny DLL, ve které došlo k chybě programu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 44ebe042ff6e2507530e4be410e768550e922b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703633"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Postupy: Hledání knihovny DLL, ve které program selhal.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce Nástroje klikněte na položku Nastavení importu a exportu. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Pokud vaše aplikace selže během volání systémové knihovny DLL nebo kódu někoho jiného, je nutné zjistit, která knihovna DLL byla aktivní, když došlo k chybě. Pokud dojde k chybě v knihovně DLL mimo vlastní program, můžete umístění identifikovat pomocí okna **moduly** .  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Zjištění, kde došlo k chybě, pomocí okna moduly  
  
1. Poznamenejte si adresu, kde došlo k chybě.  
  
2. V nabídce **ladění** vyberte možnost **Windows**a klikněte na **moduly**.  
  
3. V okně **moduly** Najděte sloupec **adresa** . Možná budete muset použít posuvník, abyste ho viděli.  
  
4. Kliknutím na tlačítko **adresa** v horní části sloupce seřadíte knihovny DLL podle adres.  
  
5. Prohledejte seřazený seznam a vyhledejte knihovnu DLL, jejíž rozsah adres obsahuje umístění selhání.  
  
6. Podívejte se na sloupce **název** a **cesta** , kde se zobrazí název a cesta ke knihovně DLL.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: ladění nativních knihoven DLL](../debugger/how-to-debug-native-dlls.md)   
 [Postupy: Použití okna Moduly](../debugger/how-to-use-the-modules-window.md)
