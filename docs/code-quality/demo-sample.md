---
title: Ukázkový C++ projekt pro analýzu kódu
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 071c16267486e1dda1e183cad3c488345974a3cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745924"
---
# <a name="sample-c-project-for-code-analysis"></a>Ukázkový C++ projekt pro analýzu kódu

Následující postupy ukazují, jak vytvořit ukázku pro [Návod: Analýza kódu C/C++ pro vady](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Postupy vytvoří:

- Řešení sady Visual Studio s názvem CppDemo.

- Statický projekt knihovny s názvem CodeDefects.

- Statický projekt knihovny s názvem poznámky.

Procedury také poskytují kód pro hlavičku a soubory *. cpp* pro statické knihovny.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Vytvoření řešení CppDemo a projektu CodeDefects

1. Klikněte na nabídku **soubor** , přejděte na příkaz **Nový**a poté klikněte na možnost **Nový projekt**.

2. V seznamu stromu **typů projektu** , není- C++ li výchozí jazyk v sadě Visual Studio a rozšířené **jiné jazyky**.

3. Rozbalte **vizuál C++** a pak klikněte na **Obecné**.

4. V nabídce **šablony**klikněte na **prázdný projekt**.

5. Do textového pole **název** zadejte **CodeDefects**.

6. Zaškrtněte políčko **vytvořit adresář pro řešení** .

7. Do textového pole **název řešení** zadejte **CppDemo**.

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurace projektu CodeDefects jako statické knihovny

1. V Průzkumník řešení klikněte pravým tlačítkem na **CodeDefects** a pak klikněte na **vlastnosti**.

2. Rozbalte položku **Vlastnosti konfigurace** a klikněte na možnost **Obecné**.

3. V seznamu **Obecné** vyberte text ve sloupci vedle položku **cílové rozšíření**a pak zadejte **. lib**.

4. V části **výchozí nastavení projektu**klikněte na sloupec vedle možnosti **typ konfigurace**a pak klikněte na **Statická knihovna lib (. lib)** .

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Přidání záhlaví a zdrojového souboru do projektu CodeDefects

1. V Průzkumník řešení rozbalte **CodeDefects**, klikněte pravým tlačítkem na **hlavičkové soubory**, klikněte na **Přidat**a pak klikněte na **Nová položka**.

2. V dialogovém okně **Přidat novou položku** klikněte na **kód**a pak klikněte na **hlavičkový soubor (. h)** .

3. Do pole **název** zadejte text **Chyba. h** a pak klikněte na tlačítko **Přidat**.

4. Zkopírujte následující kód a vložte ho do souboru *. h chyby* v editoru sady Visual Studio.

    ```cpp
    #include <windows.h>

    //
    //These 3 functions are consumed by the sample
    //  but are not defined. This project cannot be linked!
    //

    bool CheckDomain( LPCSTR );
    HRESULT ReadUserAccount();

    //
    //These constants define the common sizes of the
    //  user account information throughout the program
    //

    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

5. V Průzkumník řešení klikněte pravým tlačítkem myši na **zdrojové soubory**, přejděte na **Nový**a klikněte na **Nová položka**.

6. V dialogovém okně **Přidat novou položku** klikněte na  **C++ soubor (. cpp)** .

7. Do pole **název** zadejte text **Chyba. cpp** a potom klikněte na tlačítko **Přidat**.

8. Zkopírujte následující kód a vložte ho do souboru *Chyba. cpp* v editoru sady Visual Studio.

    ```cpp
    #include <stdlib.h>
    #include "Bug.h"

    // the user account
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";
    int len = 0;

    bool ProcessDomain()
    {
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount() )
        {

            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )
            {
                if ( g_userAccount[len] == '\\' )
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete [] domain;
                return false;
            }
            else
            {
                domain[len]='\0';
            }
            // Process domain string
            bool result = CheckDomain( domain );

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i+j;
    }
    ```

9. Klikněte na nabídku **soubor** a potom klikněte na **Uložit vše**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Přidat projekt poznámek a nakonfigurovat ho jako statickou knihovnu

1. V Průzkumník řešení klikněte na **CppDemo**, přejděte na **Přidat**a pak klikněte na **Nový projekt**.

2. V dialogovém okně **Přidat nový projekt** rozbalte položku vizuál C++, klikněte na položku **Obecné**a poté klikněte na možnost **prázdný projekt**.

3. Do textového pole **název** zadejte **Anotace**a potom klikněte na tlačítko **Přidat**.

4. V Průzkumník řešení klikněte pravým tlačítkem myši na položku **poznámky** a potom klikněte na možnost **vlastnosti**.

5. Rozbalte položku **Vlastnosti konfigurace** a klikněte na možnost **Obecné**.

6. V seznamu **Obecné** vyberte text ve sloupci vedle položku **cílové rozšíření**a pak zadejte **. lib**.

7. V části **výchozí nastavení projektu**klikněte na sloupec vedle možnosti **typ konfigurace**a pak klikněte na **Statická knihovna lib (. lib)** .

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Přidat hlavičkový soubor a zdrojový soubor do projektu poznámky

1. V Průzkumník řešení rozbalte položku **poznámky**, klikněte pravým tlačítkem myši na **hlavičkové soubory**, klikněte na **Přidat**a pak klikněte na **Nová položka**.

2. V dialogovém okně **Přidat novou položku** klikněte na **soubor hlaviček (. h)** .

3. Do pole **název** zadejte **Anotace. h** a potom klikněte na tlačítko **Přidat**.

4. Zkopírujte následující kód a vložte ho do souboru *poznámky. h* v editoru sady Visual Studio.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();

    ```

5. V Průzkumník řešení klikněte pravým tlačítkem myši na **zdrojové soubory**, přejděte na **Nový**a klikněte na **Nová položka**.

6. V dialogovém okně **Přidat novou položku** klikněte na **kód** a potom klikněte na  **C++ soubor (. cpp)** .

7. Do pole **název** zadejte **Anotace. cpp** a potom klikněte na tlačítko **Přidat**.

8. Zkopírujte následující kód a vložte ho do souboru *poznámky. cpp* v editoru sady Visual Studio.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>
    #include <windows.h>
    #include <stdlib.h>
    #include "annotations.h"

    LinkedList* AddTail( LinkedList *node, int value )
    {
        LinkedList *newNode = NULL;

        // finds the last node
        while ( node->next != NULL )
        {
            node = node->next;
        }

        // appends the new node
        newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }

    ```

9. Klikněte na nabídku **soubor** a potom klikněte na **Uložit vše**.
