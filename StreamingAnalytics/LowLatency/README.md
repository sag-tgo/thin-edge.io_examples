# Streaming Analytics Low Latency Command and Control Sample
This example demonstrates the use of Apama to average temperature sensor
values over a 10 second window. If the average temperature exceeds a threshold
(80 in this example) then an alert is sent to the cloud and a shutdown is
initiated.

## Prerequisites

Follow the setup and configuration instructions in the
[README](../README.md) file in the parent directory before running this sample.

## Running the Sample

1. Deploy the Project using `engine_deploy --outputDeployDir project <project-src-dir>`
(Take reference from [README](../README.md)) and then copy the project
directory to the `/etc/tedge/apama/project` directory on the thin-edge device.

2. Restart the Apama service on the thin-edge device with `sudo service apama restart`.
This restarts the correlator and runs the project that was copied in the previous step.

3. Run the `publisher.py` script from this directory using
Python 3 with the command `python3 publisher.py`.

4. To see the measurements that will be sent
to the cloud, run `tedge mqtt sub 'alerts/temperature'`.

5. If you have configured the thin-edge.io installation to
connect to a cloud provider, your measurements will begin appearing there.
