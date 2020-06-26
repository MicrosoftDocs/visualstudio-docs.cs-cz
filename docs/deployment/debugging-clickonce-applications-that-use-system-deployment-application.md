---
title: Ladění aplikací ClickOnce používajících System. Deployment. Application
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, debugging
- debugging, ClickOnce applications
- debugging, System.Deployment
- deploying applications [ClickOnce], debugging
ms.assetid: 86f31948-2ca8-47c0-8e8b-c2b817bbf79f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 203f1edc2e29bbbc34fb39e6aa01c1b56bf20e91
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382650"
---
# <a name="debug-clickonce-applications-that-use-systemdeploymentapplication"></a>Ladění aplikací ClickOnce používajících System. Deployment. Application
V [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] nástroji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení umožňuje konfigurovat způsob aktualizace aplikace. Pokud ale potřebujete použít a přizpůsobit pokročilé [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] funkce nasazení, budete potřebovat přístup k objektovému modelu nasazení, který poskytuje <xref:System.Deployment.Application> . Rozhraní API můžete použít <xref:System.Deployment.Application> pro pokročilé úlohy, jako například:

- Vytvoření možnosti "aktualizovat hned" v aplikaci

- Podmíněné stahování různých součástí aplikace na vyžádání

- Aktualizace integrované přímo do aplikace

- Zajištění, že klientská aplikace je vždycky aktuální

  Vzhledem k tomu, že <xref:System.Deployment.Application> rozhraní API fungují pouze v případě, že je aplikace nasazena s [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] technologií, jediný způsob, jak je ladit, je nasadit aplikaci pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , připojit k ní a pak ji ladit. Může být obtížné připojit ladicí program dostatečně včas, protože tento kód se často spouští při spuštění aplikace a před tím, než bude možné připojit ladicí program. Řešením je umístit (nebo zastavit) pro Visual Basic projekty) před kód kontroly aktualizace nebo kód na vyžádání.

  Doporučený postup ladění je následující:

1. Než začnete, ujistěte se, že je symbol (. pdb) a zdrojové soubory archivovány.

2. Nasaďte verzi 1 aplikace.

3. Vytvořte nové prázdné řešení. V nabídce **soubor** klikněte na příkaz **Nový**a potom na **projekt**. V dialogovém okně **Nový projekt** otevřete uzel **ostatní typy projektů** a potom vyberte složku **řešení sady Visual Studio** . V podokně **šablony** vyberte **prázdné řešení**.

4. Přidejte archivované zdrojové umístění do vlastností pro toto nové řešení. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel řešení a pak klikněte na **vlastnosti**. V dialogovém okně **stránky vlastností** vyberte **Ladit zdrojové soubory**a pak přidejte adresář archivovaného zdrojového kódu. V opačném případě ladicí program nalezne zastaralé zdrojové soubory, protože cesty ke zdrojovým souborům jsou zaznamenány v souboru. pdb. Pokud ladicí program používá zastaralé zdrojové soubory, zobrazí se zpráva oznamující, že se zdroj neshoduje.

5. Ujistěte se, že ladicí program může najít soubory *. pdb* . Pokud jste je nasadili s vaší aplikací, ladicí program je automaticky vyhledá. Vždy se nejprve vedle daného sestavení vyhledá. Jinak budete muset přidat cestu archivu do **umístění souborů symbolů (. pdb)** (pro přístup k této možnosti klikněte v nabídce **nástroje** na **Možnosti**, pak otevřete uzel **ladění** a klikněte na **symboly**).

6. Ladění, co se děje `CheckForUpdate` mezi `Download` / `Update` voláními metody a.

    Například kód aktualizace může být následující:

   ```vb
       Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
           If My.Application.Deployment.IsNetworkDeployed Then

               If (My.Application.Deployment.CheckForUpdate()) Then

                   My.Application.Deployment.Update()
                   Application.Restart()

               End If

           End If
       End Sub
   ```

7. Nasaďte verzi 2.

8. Pokusí se připojit ladicí program k aplikaci verze 1, protože stahuje aktualizaci verze 2. Alternativně můžete použít `System.Diagnostics.Debugger.Break` metodu nebo jednoduše `Stop` v Visual Basic. Samozřejmě byste neměli opustit volání těchto metod v produkčním kódu.

    Předpokládejme například, že vyvíjíte aplikaci model Windows Forms a máte obslužnou rutinu události pro tuto metodu s logikou aktualizace. Chcete-li provést ladění, stačí se připojit před stiskem tlačítka a pak nastavit zarážku (Ujistěte se, že jste otevřeli příslušný archivovaný soubor a nastavili zarážku).

   Použijte <xref:System.Deployment.Application.ApplicationDeployment.IsNetworkDeployed%2A> vlastnost k vyvolání <xref:System.Deployment.Application> rozhraní API pouze v případě, že je aplikace nasazena. rozhraní API by nemělo být vyvoláno během ladění v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Viz také
- <xref:System.Deployment.Application>