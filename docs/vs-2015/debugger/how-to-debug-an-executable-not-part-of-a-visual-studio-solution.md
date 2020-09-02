---
title: 'Postupy: ladění spustitelného souboru, který není součástí řešení sady Visual Studio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e33233fd313cd6a73013ce55333a860663ddb601
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704528"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Postupy: Ladění spustitelného souboru, který není součástí řešení sady Visual Studio.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V některých případech možná budete chtít ladit spustitelný soubor, který není součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Může se jednat o spustitelný soubor, který jste vytvořili mimo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo spustitelný soubor, který jste dostali od někoho jiného.  
  
 Obvyklou odpovědí k tomuto problému je spuštění spustitelného souboru mimo aplikaci Visual Studio a jeho připojení pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ladicího programu. Další informace najdete v tématu[připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Připojení k aplikaci vyžaduje některé ruční kroky, takže bude trvat několik sekund. Toto mírné zpoždění znamená, že při pokusu o ladění problému, ke kterému dojde při spuštění, se nemůžete připojit. Také pokud ladíte program, který nečeká na vstup uživatele a rychle se dokončí, možná nebudete mít čas na připojení. Pokud jste [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] nainstalovali, můžete pro takový program vytvořit projekt exe.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Vytvoření projektu EXE pro existující spustitelný soubor  
  
1. V nabídce **soubor** klikněte na **otevřít** a vyberte **projekt**.  
  
2. V dialogovém okně **Otevřít projekt** klikněte na rozevírací seznam vedle pole **název souboru** a vyberte možnost **všechny soubory projektu**.  
  
3. Vyhledejte spustitelný soubor a klikněte na tlačítko **OK**.  
  
     Tím se vytvoří dočasné řešení, které obsahuje spustitelný soubor.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Import spustitelného souboru do řešení sady Visual Studio  
  
1. V nabídce **soubor** přejděte na příkaz **Přidat projekt**a poté klikněte na položku **existující projekt**.  
  
2. V dialogovém okně **Přidat existující projekt** klikněte na rozevírací seznam vedle pole **název souboru** a vyberte možnost **všechny soubory projektu**.  
  
3. Vyhledejte a vyberte spustitelný soubor.  
  
4. Klikněte na **OK**.  
  
5. Spusťte spustitelný soubor tak, že v nabídce **ladění** vyberete příkaz pro spuštění, například **Start**.  
  
    > [!NOTE]
    > Ne všechny programovací jazyky podporují projekty EXE. Nainstalujte, [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Pokud potřebujete tuto funkci použít.  
  
     Při ladění spustitelného souboru bez zdrojového kódu jsou dostupné funkce ladění omezené bez ohledu na to, zda se připojíte ke spuštěnému spustitelnému souboru nebo přidáte spustitelný soubor do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení. Pokud byl spustitelný soubor vytvořen bez ladicích informací v kompatibilním formátu, jsou dostupné funkce dále omezeny. Pokud máte zdrojový kód, nejlepším přístupem je importovat zdrojový kód do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a vytvořit ladicí sestavení spustitelného souboru v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Soubory DBG](https://msdn.microsoft.com/91e449e9-8b65-4123-960f-2107cd1f1cfd)
