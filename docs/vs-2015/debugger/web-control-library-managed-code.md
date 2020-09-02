---
title: Knihovna webového ovládacího prvku (spravovaný kód) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031f894eb2e117a213f4f9fbbf08ac57a1512d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688165"
---
# <a name="web-control-library-managed-code"></a>Knihovna webových prvků (spravovaný kód)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablona projektu knihovny webového ovládacího prvku vytvoří knihovnu DLL. Vzhledem k tomu, že knihovna tříd je knihovna DLL, nelze ji spustit přímo. Je nutné vytvořit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stránku, která vloží ovládací prvek. Další informace najdete v tématu [šablona knihovny webového ovládacího prvku](https://msdn.microsoft.com/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Ladění knihovny webového ovládacího prvku (Metoda 1)  
  
1. Otevřete existující projekt knihovny webového ovládacího prvku nebo vytvořte nový.  
  
2. Vytvoří [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stránku, která vloží ovládací prvek.  
  
3. Na webu, který je hostitelem [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] testovacího svazku, vytvořte podadresář s názvem `/Code` .  
  
4. Zkopírujte zdrojový kód ovládacího prvku do `/Code` podadresáře.  
  
5. Otevřete zdrojový kód v `/Code` podadresáři a nastavte zarážky.  
  
6. Otevřete okno prohlížeče s adresou URL, která odkazuje na testovací svazek. Bude dosaženo zarážky v ovládacím prvku a můžete spustit ladění.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Ladění knihovny webového ovládacího prvku (Metoda 2)  
  
1. Vytvořte projekt hostitelské aplikace a projekt webového ovládacího prvku ve stejném řešení.  
  
2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na hostitelskou aplikaci a vyberte možnost **Přidat odkaz**.  
  
3. Přidejte odkaz na projekt webového ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Webové aplikace v ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)
