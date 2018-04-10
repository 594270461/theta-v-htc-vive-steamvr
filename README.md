# RICOH THETA V with HTC Vive Using SteamVR

Sample project for using RICOH THETA HTC Vive with SteamVR for telepresence applications.

The 4K video stream from the THETA V will appear in HTC headset. You can see the controllers, but I am not controlling anything right now.

You will need to modify the script to detect the webcam on your system.  In the example below, my THETA V is the sixth webcam that Unity detected.

  using UnityEngine;
  using System.Collections;

  public class webCamDetect : MonoBehaviour
  {

    void Start()
    {
      WebCamDevice[] devices = WebCamTexture.devices;
      Debug.Log("Number of web cams connected: " + devices.Length);
      for (int i = 0; i < devices.Length; i++)
      {
        Debug.Log(i + " " + devices[i].name);
      }
      string camName = devices[5].name;
      Debug.Log("The webcam name is " + camName);
      Renderer rend = this.GetComponentInChildren<Renderer>();
      WebCamTexture mycam = new WebCamTexture();

      mycam.deviceName = camName;
      rend.material.mainTexture = mycam;

      mycam.Play();
    }
  }
