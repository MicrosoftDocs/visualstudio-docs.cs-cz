---
title: Vytvoříte balíček rozšíření pomocí šablony položky balíčku rozšíření | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/27/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: chitray
ms.author: chitray
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 2e0215b22c66d6b555650e05985a674f2ad9aed4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943099"
---
# <a name="walkthrough-create-an-extension-pack"></a>Návod: Vytvoření balíčku rozšíření

Balíček rozšíření pro je sada rozšíření, které mohou být nainstalovány společně. Balíčky rozšíření umožňují snadno sdílet vaše oblíbená rozšíření s ostatními uživateli nebo sady sadu rozšíření pro konkrétní scénář.
  
## <a name="prerequisites"></a>Požadavky

Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  

Balíček rozšíření funkce je k dispozici od verze Visual Studio 15.8 ve verzi Preview 2.
  
## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Vytváření rozšíření pomocí šablony položky balíček rozšíření

Balíček rozšíření pro položky šablona vytvoří balíček rozšíření pro sadu rozšíření, které mohou být nainstalovány společně.
  
1. V **nový projekt** dialogového okna rozbalte **Visual C#** nebo **jazyka Visual Basic** a potom klikněte na tlačítko **rozšiřitelnost**. V **šablony** vyberte **projekt VSIX**. V **název** zadejte `Test Extension Pack`. Klikněte na tlačítko **OK**.  
  
2. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. Přejděte do aplikace Visual C# **rozšiřitelnost** uzel a vyberte možnost **balíček rozšíření**. Ponechte výchozí název souboru (ExtensionPack1.cs).  
  
3. Při přidání ExtensionPack1.vsext souboru, který obsahuje následující kód

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }  
   ```

4. Vsixid rozšíření, které chcete zahrnout do balíčku rozšíření můžete najít na [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Najít rozšíření, které chcete zahrnout, a klikněte na **ID kopie**. Můžete aktualizovat existující **vsixId** v uvedeném souboru nebo jiného rozšíření přidat do seznamu.

    ![Zkopírujte VsixId z Marketplace](media/vsixid-marketplace.png)

5. Sestavte projekt a nahrát rozšíření na webu Marketplace. Zobrazit [publikování rozšíření sady Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). 
    
> [!NOTE]
> Balíček rozšíření pro můžete nainstalovat pouze rozšíření, které jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo [privátní Galerie](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).
 
## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Nainstalovat balíček rozšíření z Visual Studio Marketplace

Teď, když se publikuje rozšíření, nainstalujte ho v sadě Visual Studio a ho vyzkoušeli.

1. V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace...** .

2. Klikněte na tlačítko **Online** a vyhledejte `Test Extension Pack`.

3. Klikněte na tlačítko **Stáhnout**. Rozšíření a její seznam přípon, které jsou součástí balíčku rozšíření se pak být naplánovaná instalace.

4. Následuje ukázkový balíček rozšíření pro stažení zobrazení **rozšíření a aktualizace** dialogového okna. Pokud chcete nainstalovat jenom některé z zahrnutých rozšíření v balíčku rozšíření, můžete upravit seznam rozšíření v **naplánované pro instalaci**.

    ![Stáhněte si balíček rozšíření z Marketplace](media/vside-extensionpack.png)

5. K dokončení instalace, ukončete všechny instance sady Visual Studio.

## <a name="remove-the-extension"></a>Odebrat rozšíření

Odebrat rozšíření z počítače:

1. V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace...** .

2. Vyberte `Test Extension Pack` a potom klikněte na tlačítko **odinstalovat**. Rozšíření a její seznam přípon, které jsou součástí balíčku rozšíření se pak být naplánovaná odinstalace.

3. K dokončení odinstalace, zavřete všechny instance sady Visual Studio.
