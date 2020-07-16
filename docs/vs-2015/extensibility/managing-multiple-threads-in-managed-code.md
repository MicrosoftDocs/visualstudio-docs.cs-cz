---
title: Správa více vláken ve spravovaném kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 296ef23bc512a86917920b3c3d5fbb5ec203a21e
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387015"
---
# <a name="managing-multiple-threads-in-managed-code"></a>Správa více vláken ve spravovaném kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Máte-li spravované rozšíření VSPackage, které volá asynchronní metody nebo obsahuje operace spouštěné v jiných vláknech než ve vlákně uživatelského rozhraní sady Visual Studio, měli byste postupovat podle pokynů uvedených níže. Vlákno uživatelského rozhraní lze nechat reagovat, protože nemusí čekat na dokončení práce na jiném vlákně. Svůj kód můžete zefektivnit, protože nemáte další vlákna, která zabírají místo v zásobníku, a můžete ho lépe spolehlivit a ladit, protože se vyhnete zablokování a nereagující odezvy.  
  
 Obecně můžete přepnout z vlákna uživatelského rozhraní do jiného vlákna nebo naopak. Když se metoda vrátí, aktuální vlákno je vlákno, ze kterého bylo původně voláno.  
  
> [!IMPORTANT]
> Následující pokyny používají rozhraní API v <xref:Microsoft.VisualStudio.Threading> oboru názvů, zejména <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> třídy. Rozhraní API v tomto oboru názvů jsou v nástroji novinkou [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] . Můžete získat instanci <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> z <xref:Microsoft.VisualStudio.Shell.ThreadHelper> vlastnosti `ThreadHelper.JoinableTaskFactory` .  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Přepnutí z vlákna uživatelského rozhraní do vlákna na pozadí  
  
1. Pokud jste ve vlákně uživatelského rozhraní a chcete provést asynchronní práci ve vlákně na pozadí, použijte Task. Run ():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2. Pokud jste ve vlákně uživatelského rozhraní a chcete synchronně blokovat při práci na vlákně na pozadí, použijte <xref:System.Threading.Tasks.TaskScheduler> vlastnost `TaskScheduler.Default` uvnitř <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Přepnutí z vlákna na pozadí do vlákna uživatelského rozhraní  
  
1. Pokud se nacházíte ve vlákně na pozadí a chcete něco udělat ve vlákně uživatelského rozhraní, použijte <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Můžete použít <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> metodu pro přepnutí do vlákna uživatelského rozhraní. Tato metoda odesílá zprávu do vlákna uživatelského rozhraní s pokračováním aktuální asynchronní metody a také komunikuje se zbytkem rozhraní pro dělení na vlákna, aby nastavila správnou prioritu a zabránila zablokování.  
  
     Pokud vaše metoda vlákna na pozadí není asynchronní a nemůžete ji učinit asynchronní, můžete i nadále použít `await` syntaxi pro přepnutí do vlákna uživatelského rozhraní, a to tak, že zabalíte svou práci s <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , jako v tomto příkladu:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
