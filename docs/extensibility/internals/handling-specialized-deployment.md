---
title: Zpracování specializovaného nasazení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deploying applications [Visual Studio SDK]
- specialized deployment
ms.assetid: de068b6a-e806-45f0-9dec-2458fbb486f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3c73b118f7e137847c1342fb9949c3d7dd6dd0b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863240"
---
# <a name="handle-specialized-deployment"></a>Zpracování specializovaného nasazení
Nasazení je volitelné operace pro projekty. Webový projekt, například podporuje nasazení umožňuje projektu, aktualizujte webový server. Podobně **Smart Device** projekt podporuje nasazení ke zkopírování sestavené aplikace na cílové zařízení. Podtypy projektů můžete zadat speciální nasazení chování implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> rozhraní. Toto rozhraní definuje úplnou sadu operací nasazení:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A>  
  
  Skutečné nasazení operaci je třeba provést v samostatném vlákně, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ještě rychlejší reakce na interakci uživatele. Metody, které poskytuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> jsou volány asynchronně pomocí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a provozovat na pozadí, což prostředí dotaz na stav operace nasazení v každém okamžiku nebo zastavení operace v případě potřeby. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> Operace nasazení rozhraní se označují jako prostředí, když uživatel vybere příkaz nasazení.  
  
  Upozornit na prostředí, které operace nasazení má spuštěno nebo ukončeno, potřebuje volat podtyp projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnStartDeploy%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnEndDeploy%2A> metody.  
  
  
## <a name="to-handle-a-specialized-deployment-by-a-subtype-project"></a>Zpracování specializovaného nasazení podtyp projektu  
  
-   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A> metody pro registraci prostředí k přijímání oznámení o události stavu nasazení.  
  
    ```vb  
    Private adviseSink As Microsoft.VisualStudio.Shell.EventSinkCollection = New Microsoft.VisualStudio.Shell.EventSinkCollection()  
    Public Function AdviseDeployStatusCallback(ByVal pIVsDeployStatusCallback As IVsDeployStatusCallback, _  
                                               ByRef pdwCookie As UInteger) As Integer  
  
        If pIVsDeployStatusCallback Is Nothing Then  
            Throw New ArgumentNullException("pIVsDeployStatusCallback")  
        End If  
  
        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback)  
        Return VSConstants.S_OK  
  
    End Function  
    ```  
  
    ```csharp  
    private Microsoft.VisualStudio.Shell.EventSinkCollection adviseSink = new Microsoft.VisualStudio.Shell.EventSinkCollection();  
    public int AdviseDeployStatusCallback(IVsDeployStatusCallback pIVsDeployStatusCallback,   
                                          out uint pdwCookie)  
    {  
        if (pIVsDeployStatusCallback == null)  
            throw new ArgumentNullException("pIVsDeployStatusCallback");  
  
        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback);  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A> metoda zrušit registraci prostředí k přijímání oznámení o události stavu nasazení.  
  
    ```vb  
    Public Function UnadviseDeployStatusCallback(ByVal dwCookie As UInteger) As Integer  
        adviseSink.RemoveAt(dwCookie)  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int UnadviseDeployStatusCallback(uint dwCookie)  
    {  
        adviseSink.RemoveAt(dwCookie);  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A> metody k provedení operace potvrzení, která je specifická pro vaši aplikaci.  Tato metoda se používá hlavně pro nasazení databáze.  
  
    ```vb  
    Public Function Commit(ByVal dwReserved As UInteger) As Integer  
        'Implement commit operation here.  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int Commit(uint dwReserved)  
    {  
         //Implement commit operation here.  
         return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A> metody k provedení operace vrácení zpět. Když tato metoda je volána, musí projekt nasazení provést cokoli, co je třeba vrátit zpět změny a obnovit stav projektu. Tato metoda se používá hlavně pro nasazení databáze.  
  
    ```vb  
    Public Function Commit(ByVal dwReserved As UInteger) As Integer  
        'Implement commit operation here.  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int Rollback(uint dwReserved)  
    {  
        //Implement Rollback operation here.  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A> metodou ke zjištění, zda je možné spustit operaci nasazení projektu.  
  
    ```vb  
    Public Function QueryStartDeploy(ByVal dwOptions As UInteger, ByVal pfSupported As Integer(), ByVal pfReady As Integer()) As Integer  
        If Not pfSupported Is Nothing AndAlso pfSupported.Length > 0 Then  
            pfSupported(0) = 1  
        End If  
        If Not pfReady Is Nothing AndAlso pfReady.Length > 0 Then  
            pfReady(0) = 0  
            If Not deploymentThread Is Nothing AndAlso (Not deploymentThread.IsAlive) Then  
                pfReady(0) = 1  
            End If  
        End If  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int QueryStartDeploy(uint dwOptions, int[] pfSupported, int[] pfReady)  
    {  
        if (pfSupported != null && pfSupported.Length >0)  
            pfSupported[0] = 1;  
        if (pfReady != null && pfReady.Length >0)  
        {  
            pfReady[0] = 0;  
            if (deploymentThread != null && !deploymentThread.IsAlive)  
                pfReady[0] = 1;  
        }  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A> metodou ke zjištění, zda byla úspěšně dokončena operace nasazení.  
  
    ```vb  
    Public Function QueryStatusDeploy(ByRef pfDeployDone As Integer) As Integer  
        pfDeployDone = 1  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            pfDeployDone = 0  
        End If  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int QueryStatusDeploy(out int pfDeployDone)  
    {  
        pfDeployDone = 1;  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            pfDeployDone = 0;  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A> metoda zahájit operaci nasazení v samostatném vlákně. Umístěte kód specifický pro nasazení vaší aplikace uvnitř `Deploy` metody.  
  
    ```vb  
    Public Function StartDeploy(ByVal pIVsOutputWindowPane As IVsOutputWindowPane, ByVal dwOptions As UInteger) As Integer  
        If pIVsOutputWindowPane Is Nothing Then  
            Throw New ArgumentNullException("pIVsOutputWindowPane")  
        End If  
  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            Throw New NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first")  
        End If  
  
        outputWindow = pIVsOutputWindowPane  
  
        ' Notify that deployment is about to begin and see if any user wants to cancel.  
        If (Not NotifyStart()) Then  
            Return VSConstants.E_ABORT  
        End If  
  
        operationCanceled = False  
  
        ' Create and start our thread  
        deploymentThread = New Thread(AddressOf Me.Deploy)  
        deploymentThread.Name = "Deployment Thread"  
        deploymentThread.Start()  
  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int StartDeploy(IVsOutputWindowPane pIVsOutputWindowPane, uint dwOptions)  
    {  
        if (pIVsOutputWindowPane == null)  
            throw new ArgumentNullException("pIVsOutputWindowPane");  
  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            throw new NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first");  
  
        outputWindow = pIVsOutputWindowPane;  
  
        // Notify that deployment is about to begin and see if any user wants to cancel.  
        if (!NotifyStart())  
            return VSConstants.E_ABORT;  
  
        operationCanceled = false;  
  
        // Create and start our thread  
        deploymentThread = new Thread(new ThreadStart(this.Deploy));  
        deploymentThread.Name = "Deployment Thread";  
        deploymentThread.Start();  
  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
-   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A> metoda zastavení operace nasazení. Tato metoda je volána, když uživatel stiskne klávesu **zrušit** tlačítko během procesu nasazení.  
  
    ```vb  
    Public Function StopDeploy(ByVal fSync As Integer) As Integer  
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then  
            Return VSConstants.S_OK  
        End If  
  
        outputWindow.OutputStringThreadSafe("Canceling deployment")  
        operationCanceled = True  
        If fSync <> 0 Then  
            ' Synchronous request, wait for the thread to terminate.  
            If (Not deploymentThread.Join(10000)) Then  
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread")  
                deploymentThread.Abort()  
            End If  
        End If  
  
        Return VSConstants.S_OK  
    End Function  
    ```  
  
    ```csharp  
    public int StopDeploy(int fSync)  
    {  
        if (deploymentThread != null && deploymentThread.IsAlive)  
            return VSConstants.S_OK;  
  
        outputWindow.OutputStringThreadSafe("Canceling deployment");  
        operationCanceled = true;  
        if (fSync != 0)  
        {  
            // Synchronous request, wait for the thread to terminate.  
            if (!deploymentThread.Join(10000))  
            {  
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread");  
                deploymentThread.Abort();  
            }  
        }  
  
        return VSConstants.S_OK;  
    }  
  
    ```  
  
> [!NOTE]
>  Všechny příklady kódu, které jsou uvedeny v tomto tématu jsou součástí většího příkladu v [VSSDK ukázky](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Viz také:  
 [Podtypy projektů](../../extensibility/internals/project-subtypes.md)