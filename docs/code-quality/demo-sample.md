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
ms.openlocfilehash: 84f6ddc2012617a5216c58fa0761dc100fb8942f
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75402747"
---
# <a name="sample-c-project-for-code-analysis"></a>Ukázkový C++ projekt pro analýzu kódu

Následující postupy ukazují, jak vytvořit ukázku pro [Návod: Analýza kódu C/C++ pro vady](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Postupy vytvoří:

- A [! INCLUDEvsprvs] řešení s názvem CppDemo.

- Statický projekt knihovny s názvem CodeDefects.

- Statický projekt knihovny s názvem poznámky.

Procedury také poskytují kód pro hlavičku a soubory *. cpp* pro statické knihovny.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Vytvoření řešení CppDemo a projektu CodeDefects

1. Otevřete [! INCLUDEvsprvs] a vyberte **vytvořit nový projekt**

2. Změnit filtr jazyka na**C++**

3. Vyberte **prázdný projekt** a klikněte na **Další** .

4. Do textového pole **název projektu** zadejte **CodeDefects**

5. Do textového pole **název řešení** zadejte **CppDemo** .

6. Klikněte na **Vytvořit**.

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurace projektu CodeDefects jako statické knihovny

1. V Průzkumník řešení klikněte pravým tlačítkem na **CodeDefects** a pak klikněte na **vlastnosti**.

2. Rozbalte položku **Vlastnosti konfigurace** a klikněte na možnost **Obecné**.

3. V seznamu **Obecné** změňte **typ konfigurace**na **Statická knihovna (. lib)** .

4. V seznamu **Upřesnit** změňte **příponu cílového souboru** na **. lib.**

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Přidání záhlaví a zdrojového souboru do projektu CodeDefects

1. V Průzkumník řešení rozbalte **CodeDefects**, klikněte pravým tlačítkem na **hlavičkové soubory**, klikněte na **Přidat**a pak klikněte na **Nová položka**.

2. V dialogovém okně **Přidat novou položku** klikněte na **kód**a pak klikněte na **hlavičkový soubor (. h)** .

3. Do pole **název** zadejte text **Chyba. h** a pak klikněte na tlačítko **Přidat**.

4. Zkopírujte následující kód a vložte ho do souboru *. h chyby* v editoru.

```cpp
#pragma once

#include <windows.h>

// These functions are consumed by the sample
// but are not defined. This project cannot be linked!
bool CheckDomain(LPCTSTR);
HRESULT ReadUserAccount();

// These constants define the common sizes of the
// user account information throughout the program
const int USER_ACCOUNT_LEN = 256;
const int ACCOUNT_DOMAIN_LEN = 128;
```

5. V Průzkumník řešení klikněte pravým tlačítkem myši na **zdrojové soubory**, přejděte na **Nový**a klikněte na **Nová položka**.

6. V dialogovém okně **Přidat novou položku** klikněte na  **C++ soubor (. cpp)** .

7. Do pole **název** zadejte text **Chyba. cpp** a potom klikněte na tlačítko **Přidat**.

8. Zkopírujte následující kód a vložte ho do souboru *Chyba. cpp* v editoru.

```cpp
#include "Bug.h"

// the user account
TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
int len = 0;

bool ProcessDomain()
{
    TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
    // ReadUserAccount gets a 'domain\user' input from
    //the user into the global 'g_userAccount'
    if (ReadUserAccount())
    {
        // Copies part of the string prior to the '\'
        // character onto the 'domain' buffer
        for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
        {
            if (g_userAccount[len] == '\\')
            {
                // Stops copying on the domain and user separator ('\')
                break;
            }
            domain[len] = g_userAccount[len];
        }
        if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
        {
            // '\' was not found. Invalid domain\user string.
            delete[] domain;
            return false;
        }
        else
        {
            domain[len] = '\0';
        }
        // Process domain string
        bool result = CheckDomain(domain);

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
    return i + j;
}
```

9. Klikněte na nabídku **soubor** a potom klikněte na **Uložit vše**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Přidat projekt poznámek a nakonfigurovat ho jako statickou knihovnu

1. V Průzkumník řešení klikněte na **CppDemo**, přejděte na **Přidat**a pak klikněte na **Nový projekt**.

2. V dialogovém okně **Přidat nový projekt** Změňte filtr jazyka na **C++** a vyberte **prázdný projekt** a pak klikněte na **Další**.

3. Do textového pole **název projektu** zadejte **Anotace**a potom klikněte na **vytvořit**.

4. V Průzkumník řešení klikněte pravým tlačítkem myši na položku **poznámky** a potom klikněte na možnost **vlastnosti**.

5. Rozbalte položku **Vlastnosti konfigurace** a klikněte na možnost **Obecné**.

6. V seznamu **Obecné** změňte **typ konfigurace**na a klikněte na **Statická knihovna (. lib)** .

7. V seznamu **Upřesnit** vyberte text ve sloupci vedle možnosti **cílová Přípona souboru**a pak zadejte **. lib**.


## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Přidat hlavičkový soubor a zdrojový soubor do projektu poznámky

1. V Průzkumník řešení rozbalte položku **poznámky**, klikněte pravým tlačítkem myši na **hlavičkové soubory**, klikněte na **Přidat**a pak klikněte na **Nová položka**.

2. V dialogovém okně **Přidat novou položku** klikněte na **soubor hlaviček (. h)** .

3. Do pole **název** zadejte **Anotace. h** a potom klikněte na tlačítko **Přidat**.

4. Zkopírujte následující kód a vložte ho do souboru *poznámky. h* v editoru.

```cpp
#pragma once
#include <sal.h>

struct LinkedList
{
    struct LinkedList* next;
    int data;
};

typedef struct LinkedList LinkedList;

_Ret_maybenull_ LinkedList* AllocateNode();
```

5. V Průzkumník řešení klikněte pravým tlačítkem myši na **zdrojové soubory**, přejděte na **Nový**a klikněte na **Nová položka**.

6. V dialogovém okně **Přidat novou položku** klikněte na **kód** a potom klikněte na  **C++ soubor (. cpp)** .

7. Do pole **název** zadejte **Anotace. cpp** a potom klikněte na tlačítko **Přidat**.

8. Zkopírujte následující kód a vložte ho do souboru *poznámky. cpp* v editoru.

```cpp
#include "annotations.h"

LinkedList* AddTail(LinkedList* node, int value)
{
    // finds the last node
    while (node->next != nullptr)
    {
        node = node->next;
    }

    // appends the new node
    LinkedList* newNode = AllocateNode();
    newNode->data = value;
    newNode->next = 0;
    node->next = newNode;

    return newNode;
}
```

9. Klikněte na nabídku **soubor** a potom klikněte na **Uložit vše**.


Řešení je nyní dokončeno a mělo by se sestavit bez chyb.
