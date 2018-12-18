---
title: Ukázka ukázka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2ca480078bf269e8af662d94910a5d337c13bcd8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722372"
---
# <a name="demo-sample"></a>Demonstrační ukázka
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato následující postupy ukazují, jak vytvořit vzorku pro [návod: Analýza kódu C/C++ závad](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Vytvoření postupů:  
  
- A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení s názvem CppDemo.  
  
- Projekt statické knihovny s názvem CodeDefects.  
  
- Projekt statické knihovny s názvem poznámky.  
  
  Postupy také poskytnout kód pro záhlaví a .cpp soubory pro statické knihovny.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Vytvořit CppDemo řešení a projektu CodeDefects  
  
1.  Klikněte na tlačítko **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **nový projekt**.  
  
2.  V **typy projektů** stromu seznamu, pokud aplikace Visual C++ není výchozí jazyk v sadě Visual Studio rozbalte **jiné jazyky**.  
  
3.  Rozbalte **Visual C++** a potom klikněte na tlačítko **Obecné**.  
  
4.  V **šablony**, klikněte na tlačítko **prázdný projekt**.  
  
5.  V **název** textového pole, typ **CodeDefects**.  
  
6.  Vyberte **vytvořit adresář pro řešení** zaškrtávací políčko.  
  
7.  V **název řešení** textového pole, typ **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurace projektu CodeDefects jako statickou knihovnu  
  
1.  V Průzkumníku řešení klikněte pravým tlačítkem na **CodeDefects** a potom klikněte na tlačítko **vlastnosti**.  
  
2.  Rozbalte **vlastnosti konfigurace** a potom klikněte na tlačítko **Obecné**.  
  
3.  V **Obecné** seznamu, vyberte text ve sloupci vedle **cílová přípona**a pak zadejte **lib**.  
  
4.  V **výchozí nastavení projektu**, klikněte ve sloupci vedle **typ konfigurace**a potom klikněte na tlačítko **statické knihovny Lib (.lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Přidat záhlaví a zdrojový soubor do projektu CodeDefects  
  
1.  V Průzkumníku řešení rozbalte **CodeDefects**, klikněte pravým tlačítkem na **hlavičkové soubory**, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nová položka**.  
  
2.  V **přidat novou položku** dialogové okno, klikněte na tlačítko **kód**a potom klikněte na tlačítko **soubor hlaviček (.h)**.  
  
3.  V **název** zadejte **Bug.cpp** a potom klikněte na tlačítko **přidat**.  
  
4.  Zkopírujte následující kód a vložte ho do **Bug.cpp** soubor [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editoru.  
  
    ```  
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
  
5.  V Průzkumníku řešení klikněte pravým tlačítkem na **zdrojové soubory**, přejděte na **nový**a potom klikněte na tlačítko **nová položka**.  
  
6.  V **přidat novou položku** dialogové okno, klikněte na tlačítko **soubor C++ (.cpp)**  
  
7.  V **název** zadejte **Bug.cpp** a potom klikněte na tlačítko **přidat**.  
  
8.  Zkopírujte následující kód a vložte ho do souboru Bug.h [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editoru.  
  
    ```  
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
  
9. Klikněte na tlačítko **souboru** nabídky a pak klikněte na tlačítko **Uložit vše**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Přidat projekt poznámky a nakonfiguruje ho jako statickou knihovnu  
  
1.  V Průzkumníku řešení klikněte na tlačítko **CppDemo**, přejděte na **přidat**a potom klikněte na tlačítko **nový projekt**.  
  
2.  V **přidat nový projekt** dialogové okno pole, rozbalte Visual C++, klikněte na tlačítko **Obecné**a potom klikněte na tlačítko **prázdný projekt**.  
  
3.  V **název** textového pole, typ **poznámky**a potom klikněte na tlačítko **přidat**.  
  
4.  V Průzkumníku řešení klikněte pravým tlačítkem na **poznámky** a potom klikněte na tlačítko **vlastnosti**.  
  
5.  Rozbalte **vlastnosti konfigurace** a potom klikněte na tlačítko **Obecné**.  
  
6.  V **Obecné** seznamu, vyberte text ve sloupci vedle **cílová přípona**a pak zadejte **lib**.  
  
7.  V **výchozí nastavení projektu**, klikněte ve sloupci vedle **typ konfigurace**a potom klikněte na tlačítko **statické knihovny Lib (.lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Přidat hlavičku souboru a zdrojový soubor do projektu poznámky  
  
1.  V Průzkumníku řešení rozbalte **poznámky**, klikněte pravým tlačítkem na **hlavičkové soubory**, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nová položka**.  
  
2.  V **přidat novou položku** dialogové okno, klikněte na tlačítko **soubor hlaviček (.h)**.  
  
3.  V **název** zadejte **annotations.h** a potom klikněte na tlačítko **přidat**.  
  
4.  Zkopírujte následující kód a vložte ho do **annotations.h** soubor [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editoru.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  V Průzkumníku řešení klikněte pravým tlačítkem na **zdrojové soubory**, přejděte na **nový**a potom klikněte na tlačítko **nová položka**.  
  
6.  V **přidat novou položku** dialogové okno, klikněte na tlačítko **kód** a potom klikněte na tlačítko **soubor C++ (.cpp)**  
  
7.  V **název** zadejte **annotations.cpp** a potom klikněte na tlačítko **přidat**.  
  
8.  Zkopírujte následující kód a vložte ho do **annotations.cpp** soubor [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editoru.  
  
    ```  
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
  
9. Klikněte na tlačítko **souboru** nabídky a pak klikněte na tlačítko **Uložit vše**.



