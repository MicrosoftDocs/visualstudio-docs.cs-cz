---
title: Ukázkový projekt C++ pro analýzu kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: aafbaaf682852adaea8f20a1373ea1ae4b025fad
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704860"
---
# <a name="sample-c-project-for-code-analysis"></a>Ukázkový projekt C++ pro analýzu kódu

Tato následující postupy ukazují, jak vytvořit vzorek pro [návod: kódu analyzovat C/C++ na výskyt závad](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Postupy vytvořit:

- Řešení sady Visual Studio s názvem CppDemo.

- Statické knihovny projektu s názvem CodeDefects.

- Statické knihovny projektu s názvem poznámky.

Postupy také zadejte kód pro hlavičku a *sada* soubory pro statické knihovny.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Vytvoření řešení CppDemo a CodeDefects projektu

1. Klikněte na tlačítko **soubor** nabídky, přejděte na příkaz **nový**a potom klikněte na **nový projekt**.

2. V **typy projektů** stromu seznamu, pokud Visual C++ není výchozí jazyk v sadě VS rozbalte **jiné jazyky**.

3. Rozbalte položku **Visual C++** a potom klikněte na **Obecné**.

4. V **šablony**, klikněte na tlačítko **prázdný projekt**.

5. V **název** textového pole, typ **CodeDefects**.

6. Vyberte **vytvořit adresář pro řešení** zaškrtávací políčko.

7. V **název řešení** textového pole, typ **CppDemo**.

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurace projektu CodeDefects jako statické knihovny

1. V Průzkumníku řešení klikněte pravým tlačítkem na **CodeDefects** a pak klikněte na **vlastnosti**.

2. Rozbalte položku **vlastnosti konfigurace** a pak klikněte na **Obecné**.

3. V **Obecné** seznam, vyberte text, ve sloupci vedle **přípona cílového**a pak zadejte **.lib**.

4. V **výchozí projekt**, klikněte na sloupec vedle **typ konfigurace**a potom klikněte na **statické Lib (LIB)**.

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Záhlaví a zdrojový soubor přidat do projektu CodeDefects

1. V Průzkumníku řešení rozbalte **CodeDefects**, klikněte pravým tlačítkem na **soubory hlaviček**, klikněte na tlačítko **přidat**a potom klikněte na **novou položku**.

2. V **přidat novou položku** dialogové okno, klikněte na tlačítko **kód**a potom klikněte na **soubor (hlaviček)**.

3. V **název** zadejte **Bug.h** a pak klikněte na **přidat**.

4. Zkopírujte následující kód a vložte ji do *Bug.h* souboru v editoru Visual Studio.

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

5. V Průzkumníku řešení klikněte pravým tlačítkem na **zdrojové soubory**, přejděte na příkaz **nový**a potom klikněte na **novou položku**.

6. V **přidat novou položku** dialogové okno, klikněte na tlačítko **soubor C++ ()**

7. V **název** zadejte **Bug.cpp** a pak klikněte na **přidat**.

8. Zkopírujte následující kód a vložte ji do *Bug.cpp* souboru v editoru Visual Studio.

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

9. Klikněte na tlačítko **soubor** nabídce a pak klikněte na tlačítko **Uložit vše**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Přidání poznámky projektu a nakonfigurovat ho jako statické knihovny

1. V Průzkumníku řešení klikněte na tlačítko **CppDemo**, přejděte na příkaz **přidat**a potom klikněte na **nový projekt**.

2. V **přidat nový projekt** dialogové okno pole, rozbalte položku Visual C++, klikněte na **Obecné**a potom klikněte na **prázdný projekt**.

3. V **název** textového pole, typ **poznámky**a potom klikněte na **přidat**.

4. V Průzkumníku řešení klikněte pravým tlačítkem na **poznámky** a pak klikněte na **vlastnosti**.

5. Rozbalte položku **vlastnosti konfigurace** a pak klikněte na **Obecné**.

6. V **Obecné** seznam, vyberte text, ve sloupci vedle **přípona cílového**a pak zadejte **.lib**.

7. V **výchozí projekt**, klikněte na sloupec vedle **typ konfigurace**a potom klikněte na **statické Lib (LIB)**.

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Přidejte soubor hlaviček a zdrojového souboru do projektu poznámky

1. V Průzkumníku řešení rozbalte **poznámky**, klikněte pravým tlačítkem na **soubory hlaviček**, klikněte na tlačítko **přidat**a potom klikněte na **novou položku**.

2. V **přidat novou položku** dialogové okno, klikněte na tlačítko **soubor (hlaviček)**.

3. V **název** zadejte **annotations.h** a pak klikněte na **přidat**.

4. Zkopírujte následující kód a vložte ji do *annotations.h* souboru v editoru Visual Studio.

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

5. V Průzkumníku řešení klikněte pravým tlačítkem na **zdrojové soubory**, přejděte na příkaz **nový**a potom klikněte na **novou položku**.

6. V **přidat novou položku** dialogové okno, klikněte na tlačítko **kód** a pak klikněte na tlačítko **soubor C++ ()**

7. V **název** zadejte **annotations.cpp** a pak klikněte na **přidat**.

8. Zkopírujte následující kód a vložte ji do *annotations.cpp* souboru v editoru Visual Studio.

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

9. Klikněte na tlačítko **soubor** nabídce a pak klikněte na tlačítko **Uložit vše**.
