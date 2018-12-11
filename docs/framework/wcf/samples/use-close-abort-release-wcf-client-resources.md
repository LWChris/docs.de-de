---
title: Verwenden Sie schließen "und" Abort um WCF-Client-Ressourcen freizugeben.
description: Dispose kann Fehler und Ausnahmen auslösen, wenn Netzwerkprobleme auftreten. Die kann unerwünschtes Verhalten führen. Stattdessen verwenden Sie, schließen, und abgebrochen Sie wird, um die Clientressourcen freigeben, wenn das Netzwerk ein Fehler aufgetreten ist.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: d37ad9d2277fea2656311a5a1f57d51343d10d89
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147215"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="26316-105">Schließen und Abbruch Freigeben von Ressourcen sicher verwendet werden, wenn Netzwerkverbindungen gelöscht haben</span><span class="sxs-lookup"><span data-stu-id="26316-105">Close and Abort release resources safely when network connections have dropped</span></span>
<span data-ttu-id="26316-106">Dieses Beispiel veranschaulicht die Verwendung der `Close` und `Abort` Methoden zum Bereinigen von Ressourcen für die Verwendung eines typisierten Clients.</span><span class="sxs-lookup"><span data-stu-id="26316-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="26316-107">Die `using` Anweisung Ausnahmen verursacht, wenn die Netzwerkverbindung nicht robust ist.</span><span class="sxs-lookup"><span data-stu-id="26316-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="26316-108">Dieses Beispiel basiert auf der [Einstieg](../../../../docs/framework/wcf/samples/getting-started-sample.md) , das einen rechnerdienst implementiert.</span><span class="sxs-lookup"><span data-stu-id="26316-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="26316-109">In diesem Beispiel ist der Client eine Konsolenanwendung (.exe), und der Dienst wird von IIS (Internet Information Services, Internetinformationsdienste) gehostet.</span><span class="sxs-lookup"><span data-stu-id="26316-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26316-110">Die Setupprozedur und die Buildanweisungen für dieses Beispiel befinden sich am Ende dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="26316-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="26316-111">In diesem Beispiel werden zwei häufige Probleme veranschaulicht, die beim Verwenden der C#-Anweisung "using" mit typisierten Clients auftreten. Außerdem wird Code bereitgestellt, mit dem die Bereinigung nach Ausnahmen korrekt ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="26316-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="26316-112">Die C#-Anweisung "using" führt zu einem Aufruf von `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="26316-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="26316-113">Dies ist das Gleiche wie `Close`(). Dies kann zu Ausnahmen führen, wenn ein Netzwerkfehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="26316-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="26316-114">Da der Aufruf von `Dispose`() implizit an der schließenden Klammer des "using"-Blocks erfolgt, wird diese Quelle für Ausnahmen beim Schreiben oder Lesen des Codes häufig nicht bemerkt.</span><span class="sxs-lookup"><span data-stu-id="26316-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="26316-115">Dies stellt eine potenzielle Quelle für Anwendungsfehler dar.</span><span class="sxs-lookup"><span data-stu-id="26316-115">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="26316-116">Das erste Problem (in der `DemonstrateProblemUsingCanThrow`-Methode dargestellt) liegt darin, dass die schließende Klammer eine Ausnahme auslöst und der Code nach der schließenden Klammer nicht ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="26316-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="26316-117">Selbst wenn nichts im using-Block eine Ausnahme auslöst oder alle Ausnahmen im using-Block abgefangen werden, wird `Console.Writeline` möglicherweise nicht ausgeführt, da der implizite `Dispose`()-Aufruf an der schließenden Klammer eine Ausnahme auslösen kann.</span><span class="sxs-lookup"><span data-stu-id="26316-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="26316-118">Das zweite Problem (in der `DemonstrateProblemUsingCanThrowAndMask`-Methode veranschaulicht) ist eine weitere Implikation der schließenden Klammer, die eine Ausnahme auslöst:</span><span class="sxs-lookup"><span data-stu-id="26316-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="26316-119">Da `Dispose`() in einem "finally"-Block auftritt, tritt `ApplicationException` nur außerhalb des using-Blocks auf, wenn bei `Dispose`() ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="26316-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="26316-120">Wenn der Code außen wissen muss, wann die `ApplicationException` auftritt, kann das "using"-Konstrukt zu Problemen führen, da diese Ausnahme maskiert wird.</span><span class="sxs-lookup"><span data-stu-id="26316-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="26316-121">Abschließend wird im Beispiel veranschaulicht, wie die Bereinigung ordnungsgemäß ausgeführt wird, nachdem Ausnahmen in `DemonstrateCleanupWithExceptions` aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="26316-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="26316-122">Dabei wird ein try/catch-Block verwendet, um Fehler zu melden und `Abort` aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="26316-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="26316-123">Finden Sie unter den [Ausnahmen erwartet](../../../../docs/framework/wcf/samples/expected-exceptions.md) Weitere Informationen zum Abfangen von Ausnahmen von clientaufrufen.</span><span class="sxs-lookup"><span data-stu-id="26316-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="26316-124">Die using-Anweisung und ServiceHost: Viele selbst gehostete Anwendungen nur wenig mehr als einen Dienst hosten, und ServiceHost.Close nur selten eine Ausnahme auslöst, damit die Verwendung solcher Anwendungen sicher verwenden können-Anweisung mit ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="26316-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="26316-125">Achten Sie jedoch darauf, dass ServiceHost.Close eine `CommunicationException` auslösen kann. Wenn die Anwendung daher nach dem Schließen von ServiceHost fortgesetzt wird, sollten Sie die Verwendung der using-Anweisung vermeiden und sich an das zuvor beschriebene Muster halten.</span><span class="sxs-lookup"><span data-stu-id="26316-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="26316-126">Wenn Sie das Beispiel ausführen, werden die Antworten und Ausnahmen für den Vorgang im Konsolenfenster des Clients angezeigt.</span><span class="sxs-lookup"><span data-stu-id="26316-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="26316-127">Im Clientprozess werden drei Szenarios ausgeführt, die jeweils versuchen, `Divide` aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="26316-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="26316-128">Im ersten Szenario wird veranschaulicht, dass Code aufgrund einer Ausnahme von `Dispose`() übersprungen wird.</span><span class="sxs-lookup"><span data-stu-id="26316-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="26316-129">Im zweiten Szenario wird veranschaulicht, dass eine wichtige Ausnahme aufgrund einer Ausnahme von `Dispose`() maskiert wird.</span><span class="sxs-lookup"><span data-stu-id="26316-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="26316-130">Das dritte Szenario zeigt die ordnungsgemäße Bereinigung.</span><span class="sxs-lookup"><span data-stu-id="26316-130">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="26316-131">Die erwartete Ausgabe vom Clientprozess lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="26316-131">The expected output from the client process is:</span></span>  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="26316-132">So können Sie das Beispiel einrichten, erstellen und ausführen</span><span class="sxs-lookup"><span data-stu-id="26316-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="26316-133">Stellen Sie sicher, dass Sie ausgeführt haben die [Schritte der Einrichtung einmaligen Setupverfahren für Windows Communication Foundation-Beispiele](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26316-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="26316-134">Um die C#- oder Visual Basic .NET-Edition der Projektmappe zu erstellen, befolgen Sie die unter [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)aufgeführten Anweisungen.</span><span class="sxs-lookup"><span data-stu-id="26316-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="26316-135">Um das Beispiel in einer einzelnen oder computerübergreifenden Konfiguration ausführen möchten, folgen Sie den Anweisungen im [Ausführen der Windows Communication Foundation-Beispiele](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26316-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="26316-136">Die Beispiele sind möglicherweise bereits auf dem Computer installiert.</span><span class="sxs-lookup"><span data-stu-id="26316-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="26316-137">Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="26316-137">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="26316-138">Wenn dieses Verzeichnis nicht vorhanden ist, fahren Sie mit [Windows Communication Foundation (WCF) und Windows Workflow Foundation (WF) Samples für .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) alle Windows Communication Foundation (WCF) herunterladen und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Beispiele.</span><span class="sxs-lookup"><span data-stu-id="26316-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="26316-139">Dieses Beispiel befindet sich im folgenden Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="26316-139">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="26316-140">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="26316-140">See Also</span></span>