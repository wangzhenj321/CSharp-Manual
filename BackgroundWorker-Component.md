## Properties

### CancellationPending

Gets a value indicating whether the application has requested cancellation of a background operation.

## Methods

### RunWorkerAsync(Object)

Starts execution of a background operation.

The RunWorkerAsync method submits a request to start the operation running asynchronously. When the request is serviced, the DoWork event is raised, which in turn starts execution of your background operation.

If your operation requires a parameter, you can provide it as the argument parameter to RunWorkerAsync. (Object \-\> DoWorkEventArgs.Argument)

If the background operation is already running, calling RunWorkerAsync again will raise an InvalidOperationException.

### ReportProgress(Int32, Object)

Raises the ProgressChanged event.

If you need the background operation to report on its progress, you can call the ReportProgress method to raise the ProgressChanged event (Object \-\> ProgressChangedEventArgs.UserState). The WorkerReportsProgress property value must true, or ReportProgress will throw an InvalidOperationException.

It is up to you to implement a meaningful way of measuring your background operation's progress as a percentage of the total task completed.

## Events

### DoWork

Occurs when RunWorkerAsync is called.

This event is raised when you call the RunWorkerAsync method. This is where you start the operation that performs the potentially time-consuming work.

Your code in the DoWork event handler should periodically check the CancellationPending property value and abort the operation if it is true. When this occurs, you can set the Cancel flag of System.ComponentModel.DoWorkEventArgs to true, and the Cancelled flag of System.ComponentModel.RunWorkerCompletedEventArgs in your RunWorkerCompleted event handler will be set to true.

### ProgressChanged

Occurs when ReportProgress is called.

### RunWorkerCompleted

Occurs when the background operation has completed, has been canceled, or has raised an exception.

This event is raised when the DoWork event handler returns.

If the operation completes successfully and its result is assigned in the DoWork event handler, you can access the result through the RunWorkerCompletedEventArgs.Result property.

The Error property of System.ComponentModel.RunWorkerCompletedEventArgs indicates that an exception was thrown by the operation.

The Cancelled property of System.ComponentModel.RunWorkerCompletedEventArgs indicates whether a cancellation request was processed by the background operation. If your code in the DoWork event handler detects a cancellation request by checking the CancellationPending flag and setting the Cancel flag of System.ComponentModel.DoWorkEventArgs to true, the Cancelled flag of System.ComponentModel.RunWorkerCompletedEventArgs also will be set to true.

## References

1. [Walkthrough: Multithreading with the BackgroundWorker Component (C#)](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component)

2. [BackgroundWorker Class](https://msdn.microsoft.com/en-us/library/system.componentmodel.backgroundworker(v=vs.110).aspx)