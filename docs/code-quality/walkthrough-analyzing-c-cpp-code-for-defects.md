---
title: 'Návod: Analýza kódu C/C++ na výskyt závad'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6e15c6acc241e36e7cadc1d6f043549f1f5e46c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922030"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Návod: Analýza kódu C/C++ na výskyt závad

Tento návod ukazuje, jak analyzovat kódu C/C++ pro potenciální defekty kódu pomocí nástroje Analýza kódu pro kód C/C++.

- Spuštění analýzy kódu v nativním kódu.
- Analýza kódu vadou upozornění.
- Zpracovávat upozornění za chybu.
- Přidání poznámek ke zdrojového kódu ke zlepšení analýza vadou kódu.

## <a name="prerequisites"></a>Požadavky

- Kopii [Demo-ukázka](../code-quality/demo-sample.md).
- Základní znalosti jazyka C/C++

### <a name="to-run-code-defect-analysis-on-native-code"></a>Ke spuštění vadou analýza kódu v nativním kódu

1. Otevřete ukázku řešení v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

     Ukázkové řešení teď naplní **Průzkumníku řešení**.

2. Na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit řešení**.

     Řešení sestavení bez jakýchkoli chyb nebo upozornění.

3. V **Průzkumníku**, vyberte CodeDefects projekt.

4. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

     **Stránky vlastností CodeDefects** se zobrazí dialogové okno.

5. Klikněte na tlačítko **analýza kódu**.

6. Klikněte **povolit analýzy kódu pro C/C++ v sestavení** zaškrtávací políčko.

7. Znovu sestavte projekt CodeDefects.

     Upozornění analýzy kódu se zobrazí v **seznam chyb**.

### <a name="to-analyze-code-defect-warnings"></a>K analýze upozornění vadou kódu

1. Na **zobrazení** nabídky, klikněte na tlačítko **seznam chyb**.

     V závislosti na vývojáře profil, který jste zvolili v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], možná budete muset přejděte na příkaz **ostatní okna** na **zobrazení** nabídce a pak klikněte na tlačítko **seznam chyb**.

2. V **seznam chyb**, dvakrát klikněte na následující upozornění:

     upozornění C6230: implicitní přetypování mezi sémanticky různé typy: pomocí HRESULT v kontextu, logická hodnota.

     Editor kódu zobrazí řádek, který způsobil upozornění ve funkci `bool``ProcessDomain()`. Toto upozornění určuje, že HRESULT je použit v příkazu 'if' kde je očekávána logickou.

3. Opravte toto upozornění pomocí makro bylo úspěšné. Váš kód by měl vypadat následující kód:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. V **seznam chyb**, dvakrát klikněte na následující upozornění:

     upozornění C6282: nesprávné operátor: přiřazení konstantu v kontextu testu. Byl == určený?

5. Opravte toto upozornění testování rovnosti. Váš kód by měl vypadat podobně jako následující kód:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>Chcete-li upozornění považovat za chybu

1. V souboru Bug.cpp, přidejte následující `#pragma` příkaz na začátek souboru, který se má upozornění C6001 považovat za chybu:

   ```cpp
   #pragma warning (error: 6001)
   ```

2. Znovu sestavte projekt CodeDefects.

     V **seznam chyb**, C6001 se zobrazí jako chyba.

3. Opravte chyby zbývající dva C6001 v **seznam chyb** podle inicializace `i` a `j` na hodnotu 0.

4. Znovu sestavte projekt CodeDefects.

     Sestavení projektu bez žádná upozornění ani chyby.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Chcete-li opravit upozornění zdrojového kódu poznámky v annotation.c

1. V Průzkumníku řešení vyberte projekt poznámky.

2. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

     **Stránky vlastností poznámky** se zobrazí dialogové okno.

3. Klikněte na tlačítko **analýza kódu**.

4. Vyberte **povolit analýzy kódu pro C/C++ v sestavení** zaškrtávací políčko.

5. Znovu sestavte projekt poznámky.

6. V **seznam chyb**, dvakrát klikněte na následující upozornění:

     upozornění C6011: vyhodnocení ukazatele NULL 'newNode'.

     Toto upozornění označuje selhání volající Zkontrolujte návratovou hodnotu. V tomto případě volání **AllocateNode** může vrátit hodnotu NULL (viz soubor hlaviček annotations.h pro funkce deklaraci pro AllocateNode).

7. Otevřete soubor annotations.cpp.

8. Chcete-li toto upozornění, použijte k testování návratovou hodnotu příkazem 'if'. Váš kód by měl vypadat následující kód:

   ```cpp
   if (NULL != newNode)
   {
   newNode->data = value;
   newNode->next = 0;
   node->next = newNode;
   }
   ```

9. Znovu sestavte projekt poznámky.

     Sestavení projektu bez žádná upozornění ani chyby.

### <a name="to-use-source-code-annotation"></a>Použití nástroje zdrojového kódu

1. Přidání poznámek ke formální parametry a vrátí hodnotu funkce `AddTail` pomocí předběžné a Post podmínky, jak je uvedeno v tomto příkladu:

   ```cpp
   [returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail
   (
   [SA_Pre(Null=SA_Maybe)] LinkedList* node,
   int value
   )
   ```

2. Znovu sestavte projekt poznámky.

3. V **seznam chyb**, dvakrát klikněte na následující upozornění:

     upozornění C6011: Při přesměrování NULOVÝ ukazatel 'uzlu'.

     Toto upozornění označuje, že uzel předaný funkci může mít hodnotu null a označuje číslo řádku, kde byla vyvolána upozornění.

4. Chcete-li toto upozornění, použijte k testování návratovou hodnotu příkazem 'if'. Váš kód by měl vypadat následující kód:

   ```cpp
   . . .
   LinkedList *newNode = NULL;
   if (NULL == node)
   {
        return NULL;
        . . .
   }
   ```

5. Znovu sestavte projekt poznámky.

     Sestavení projektu bez žádná upozornění ani chyby.

## <a name="see-also"></a>Viz také

[Návod: Analýza spravovaného kódu na výskyt závad kódu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[analýza kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)