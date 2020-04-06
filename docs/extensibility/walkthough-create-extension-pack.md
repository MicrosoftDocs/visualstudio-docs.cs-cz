---
title: Vytvoření rozšíření pack se šablonou položky rozšíření pack | Dokumenty společnosti Microsoft
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697753"
---
# <a name="walkthrough-create-an-extension-pack"></a>Návod: Vytvoření balíčku rozšíření

Rozšíření Pack je sada rozšíření, které lze nainstalovat společně. Rozšiřující balíčky umožňují snadno sdílet oblíbená rozšíření s ostatními uživateli nebo spojit sadu rozšíření pro konkrétní scénář.

## <a name="prerequisites"></a>Požadavky

Počínaje Visual Studio 2015, Visual Studio SDK je součástí volitelné funkce v nastavení Sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

Funkce Extension Pack je k dispozici od Visual Studia 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Vytvoření rozšíření se šablonou položky balíčku rozšíření

Šablona položky rozšíření pack vytvoří rozšíření pack se sadou rozšíření, které lze nainstalovat společně.

1. V dialogovém okně **Nový projekt** vyhledejte "vsix" a vyberte **VSIX Project**. Do **pole Název projektu**zadejte "Test Extension Pack". Vyberte **Vytvořit**.

2. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. Přejděte do uzlu **rozšiřitelnosti** visual c# a vyberte **rozšíření balíčku**. Ponechte výchozí název souboru (ExtensionPack1.cs).

3. Je přidán soubor ExtensionPack1.vsext, který obsahuje následující kód

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

4. Vsixid rozšíření zahrnout do rozšíření pack lze nalézt na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/). Najděte rozšíření, které chcete zahrnout, a klikněte na **Kopírovat ID**. Můžete aktualizovat existující **vsixId** ve výše uvedeném souboru nebo přidat další rozšíření do seznamu.

    ![Kopírovat VsixId z marketplace](media/vsixid-marketplace.png)

5. Sestavte projekt a nahrajte rozšíření na Marketplace. Viz [Publikování rozšíření Sady Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Balíček rozšíření můžete nainstalovat pouze rozšíření, které jsou k dispozici na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo soukromé [galerie](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Instalace sady Extension Pack z webu Visual Studio Marketplace

Teď, když je rozšíření publikováno, nainstalujte ho do sady Visual Studio a otestujte jej tam.

::: moniker range="vs-2017"

1. V sadě Visual Studio klikněte v nabídce **Nástroje** na **položku Rozšíření a aktualizace**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V sadě Visual Studio klikněte v nabídce **Rozšíření** na **položku Spravovaná rozšíření**.

::: moniker-end

2. Klikněte na **Online** a vyhledejte "Test Extension Pack".

3. Klepněte na tlačítko **Stáhnout**. Rozšíření a jeho seznam rozšíření zahrnutých v rozšíření pack u následných okolností bude naplánováno k instalaci.

4. Níže je ukázka rozšíření Pack stáhnout zobrazení dialogového okna **Spravovat rozšíření.** Pokud dáváte přednost instalaci pouze některých zahrnutých rozšíření v balíčku Rozšíření, můžete upravit seznam rozšíření v **naplánované instalaci**.

    ![Stáhnout balíček rozšíření z Marketplace](media/vside-extensionpack.png)

5. Chcete-li dokončit instalaci, zavřete všechny instance sady Visual Studio.

## <a name="remove-the-extension"></a>Odebrání rozšíření

Odebrání rozšíření z počítače:

::: moniker range="vs-2017"

1. V sadě Visual Studio klikněte v nabídce **Nástroje** na **položku Rozšíření a aktualizace**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V sadě Visual Studio klikněte v nabídce **Rozšíření** na **položku Spravovaná rozšíření**.

::: moniker-end

2. Vyberte **test rozšíření Pack** a klepněte na tlačítko **Odinstalovat**. Rozšíření a jeho seznam rozšíření zahrnutých v rozšíření pack u následných bude naplánováno na odinstalaci.

3. Chcete-li provést odinstalaci, zavřete všechny instance sady Visual Studio.
