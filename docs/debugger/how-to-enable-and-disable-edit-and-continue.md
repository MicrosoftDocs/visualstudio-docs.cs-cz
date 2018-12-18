---
title: 'Postupy: povolení a zákaz operace upravit a pokračovat | Dokumentace Microsoftu'
ms.custom: seodec18
ms.date: 10/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 0b5fbc7ee0f2d85c72ccda75bc2e8531419d52e3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051384"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Postupy: povolení a zákaz operace upravit a pokračovat (C#, VB, C++)

Můžete zakázat nebo povolit **upravit a pokračovat** v sadě Visual Studio **možnosti** dialogové okno v době návrhu. **Upravit a pokračovat** sestavení lze použít pouze v ladění. Další informace najdete v tématu [upravit a pokračovat](../debugger/edit-and-continue.md). 
  
Pro nativní kód C++ **upravit a pokračovat** vyžaduje použití `/INCREMENTAL` možnost. Další informace o požadavcích na funkci v jazyce C++, naleznete v tomto [blogový příspěvek](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) a [upravit a pokračovat (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
**K povolení nebo zakázání funkce upravit a pokračovat:**  
  
1.  Pokud jste v relaci ladění, zastavte ladění (**ladění** > **Zastavit ladění** nebo **Shift**+**F5**) .

1.  V **nástroje** > **možnosti** > (nebo **ladění** > **možnosti**) > **ladění**  >  **Obecné**vyberte **upravit a pokračovat** v pravém podokně.  
  
    > [!NOTE]
    >  Pokud je povolená technologie IntelliTrace a shromažďovat události IntelliTrace a informace o volání, upravit a pokračovat je zakázané. Další informace najdete v tématu [IntelliTrace](../debugger/intellitrace.md).
    
1.  Pro kód jazyka C++, ujistěte se, že **Povolit nativní editovat a pokračovat** je vybraná a nastavit další možnosti:
    - **Použít změny při pokračování (jenom nativní)**  
      
      Pokud vybraná, Visual Studio automaticky zkompiluje a platí změn kódu, pokud budete pokračovat v ladění ze stavu pozastavení. V opačném případě můžete také použít změny pomocí **ladění** > **použít změny kódu**.  
      
    - **Upozornit na starý kód (pouze nativní)**  
      
      Pokud je vybrána, poskytuje upozornění na starý kód. 
  
1.  Klikněte na tlačítko **OK**.    
