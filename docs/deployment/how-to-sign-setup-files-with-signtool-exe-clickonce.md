---
title: Postup při podepisování instalačních souborů pomocí SignTool.exe (ClickOnce) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9e1911b6e86058b7f078f40fa10ca5e0e4e53c0
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382065"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Postupy: Podepsání instalačních souborů pomocí SignTool.exe (ClickOnce)
K podepsání instalačního programu (*setup.exe*) můžete použít *SignTool.exe* . Tento proces pomáhá zajistit, aby v počítačích koncových uživatelů nebyly nainstalovány neoprávněné soubory.

 Ve výchozím nastavení má ClickOnce podepsané manifesty a program s podepsaným nastavením. Pokud však chcete později změnit parametry instalačního programu, je nutné program podepsat později. Pokud změníte parametry po podepsání instalačního programu, podpis bude poškozen.

 Následující procedura generuje nepodepsané manifesty a nepodepsaný instalační program. V aplikaci Visual Studio je pak podepisování ClickOnce povoleno pro generování podepsaných manifestů. Instalační program je ponechán bez znaménka, aby zákazník mohl podepsat spustitelný soubor pomocí vlastního certifikátu.

### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Vygenerujte nepodepsaný instalační program a podepište se později.

1. Ve vývojovém počítači nainstalujte certifikát, ve kterém chcete manifest podepsat.

2. Vyberte projekt v **Průzkumník řešení**.

3. V nabídce **projekt** klikněte na vlastnosti *ProjectName* **Properties**.

4. Na stránce **podepisování** zrušte **podpis manifestů ClickOnce**.

5. Na stránce **publikovat** klikněte na **požadované součásti**.

6. Ověřte, že jsou vybrané všechny požadavky, a pak klikněte na **OK**.

7. Na stránce **publikovat** ověřte nastavení publikování a pak klikněte na **Publikovat nyní**.

     Řešení publikuje nepodepsaný manifest aplikace, nepodepsaný manifest nasazení, soubory pro konkrétní verzi a nepodepsaný instalační program do umístění složky pro publikování.

8. Na stránce **publikovat** klikněte na **požadované součásti**.

9. V dialogovém okně **požadavky** zrušte zaškrtnutí políčka **vytvořit instalační program a nainstalujte požadované součásti**.

10. Na stránce **publikovat** ověřte nastavení publikování a pak klikněte na **Publikovat nyní**.

     Řešení publikuje podepsaný manifest aplikace, podepsaný manifest nasazení a soubory specifické pro verzi do umístění složky pro publikování. Proces publikování nepřepíše nepodepsaný instalační program.

11. Na webu zákazníka otevřete příkazový řádek.

12. Přejděte do adresáře, který obsahuje soubor *. exe* .

13. Podepište soubor *. exe* pomocí následujícího příkazu:

    ```cmd
    signtool sign /sha1 CertificateHash Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

     Chcete-li například podepsat instalační program, použijte jeden z následujících příkazů:

    ```cmd
    signtool sign /sha1 CCB... Setup.exe
    signtool sign /f CertFileName Setup.exe
    ```

## <a name="see-also"></a>Viz také
- [Postupy: Opětovné podepsání manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
