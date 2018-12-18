---
title: 'Postupy: podepsání souborů instalace pomocí SignTool.exe (ClickOnce) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b66d9440ebcf62c59049b45769a2244fc773480e
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081498"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Postupy: podepsání souborů instalace pomocí SignTool.exe (ClickOnce)
Můžete použít *SignTool.exe* podepsat instalační program (*setup.exe*). Tento proces pomáhá zajistit, že zmanipulovanou soubory nejsou nainstalované v počítačích koncových uživatelů.  
  
 Ve výchozím nastavení má ClickOnce podepsané manifesty a podepsaný instalační program. Nicméně pokud chcete změnit parametry instalační program později, musíte podepsat instalační program později. Pokud změníte parametry po instalační program je podepsán, dojde k poškození podpis.  
  
 Následující postup vytvoří nepodepsané manifesty a bez znaménka instalační program. Potom ClickOnce je povoleno podepisování v sadě Visual Studio ke generování podepsané manifesty. Instalační program, zůstane bez znaménka, aby zákazník mohli podepsat spustitelný soubor s vlastní certifikát.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Generovat nepodepsané instalační program a podepsání později  
  
1.  Ve vývojovém počítači, nainstalujte certifikát, který chcete podepsat manifesty s.  
  
2.  Vyberte projekt v **Průzkumníka řešení**.  
  
3.  Na **projektu** nabídky, klikněte na tlačítko *ProjectName* **vlastnosti**.  
  
4.  V **podepisování** zrušte **podepsat manifesty ClickOnce**.  
  
5.  V **publikovat** klikněte na **požadavky**.  
  
6.  Ověřte, zda jsou vybrány všechny požadavky a klikněte na **OK**.  
  
7.  V **publikovat** stránce, ověřte nastavení publikování a pak klikněte na tlačítko **publikovat**.  
  
     Řešení publikuje manifestu nepodepsané aplikace, manifest nasazení bez znaménka, specifické pro verzi soubory a bez znaménka instalační program do umístění složky pro publikování.  
  
8.  V **publikovat** klikněte na **požadavky**.  
  
9. V **požadavky** dialogové okno, zrušte zaškrtnutí **vytvořit instalační program pro nainstalování nezbytných součástí**.  
  
10. V **publikovat** stránce, ověřte nastavení publikování a pak klikněte na tlačítko **publikovat**.  
  
     Řešení publikuje manifestu podepsanou aplikaci, podepsaný manifest nasazení a specifické pro verzi soubory do umístění složky pro publikování. Proces publikování není přepsán instalačního programu bez znaménka.  
  
11. Na webu zákazníka otevřete příkazový řádek.  
  
12. Přejděte do adresáře, který obsahuje *.exe* souboru.  
  
13. Přihlaste *.exe* soubor pomocí následujícího příkazu:  
  
    ```cmd  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Například k podepisování instalačního programu, použijte jednu z následujících příkazů:  
  
    ```cmd  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Opětovné podepisování manifestů aplikace a nasazení](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
